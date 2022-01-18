---
title: "How to Add Search to Your Hugo Static Site 🔎"
date: 2022-01-08T12:49:27+06:00
writtenDate: "January 8, 2022"
authors: "Anthony Dellavecchia"
featureImage: images/blog/algolia.png
postImage: images/blog/algolia.png
tags: ["javascript", "how-to", "webdev"]
---

> **TLDR:** Use Algolia to create fast searching of your website's static pages. This tutorial is for sites using Hugo.

If you view my [Blog section](https://anthonydellavecchia.com/blog), you'll see a search bar that I've just added.

![Image](/images/blog/search.png)

After writing multiple [blog posts](https://anthonydellavecchia.com/blog), I quickly realized that more pages meant more clutter. If someone wants to find a post, they'd have to manually search for it by digging through each page. Imagine if I have 10 pages, with 6 blog posts per page. Finding an article would be difficult and a bad user experience. Adding a search bar, as well as tag filters, would fix this issue, so I did some research on how to implement this for [my website](https://anthonydellavecchia.com/).

I'm using Hugo as my static site generator and the documentation isn't the best. Their [docs](https://gohugo.io/tools/search/) show multiple options for implementing search, but their explanations are pretty bad. Some options include: using native Javascript, Elasticsearch, lunr.js, etc. But I went with a third-party service, called Algolia, just because I found the documentation to be great.

## Summary

To enable searching on a static site, you need to first create a JSON search index which acts as a database for your search results. From there, you update this JSON search index each time you update/create new pages. Then, you access/query the data by using REST API's provided by Algolia. Finally, you display the results on your page.

## Getting Started

The first thing to do is [sign up for a free](https://www.algolia.com/users/sign_up) Algolia account (since we're using this service). Algolia is nice because they have great documentation, built-in widgets, provides fast results, and is easy to implement.

## Generate JSON Search Index

### Configure Output to JSON

Hugo can output content into multiple different file formats (like javascript, xml, toml, etc.). So, we want to set up our project to output JSON. Do this by configuring the `config.toml/yaml`:

**config.toml**

{{< highlight toml >}}
[outputFormats.Algolia]
baseName = "algolia"
isPlainText = true
mediaType = "application/json"
notAlternative = true

[params.algolia]
vars = ["title", "summary", "date", "publishdate", "permalink"]
params = ["tags"]

[outputs]
home = ["HTML", "Algolia"]
{{< /highlight >}}

Here, we are creating a custom outputFormat called Algolia, which is of type JSON. We're also giving it some variables which will be used later.

### Creating a Search Index Template

Next, create a file which will generate the JSON search index output. This file is the template for creating our output JSON. In the `layouts/` directory, create a file like: `search-index.json`.

**search-index.json**

{{< highlight json >}}
{{- $.Scratch.Add "index" slice -}}

{{- range where .Site.RegularPages ".Type" "blog" -}}

    {{- $.Scratch.Add "index" (dict "objectID" .UniqueID "date" .Date.UTC.Unix "fuzzywordcount" .FuzzyWordCount "kind" .Kind "lastmod" .Lastmod.UTC.Unix "permalink" .Permalink "publishdate" .PublishDate "readingtime" .ReadingTime "relpermalink" .RelPermalink "summary" .Summary "title" .Title "type" .Type "url" .RelPermalink "wordcount" .WordCount "section" .Section "tags" .Params.Tags "authors" .Params.Authors "image" .Params.FeatureImage "writtendate" .Params.WrittenDate)}}

{{- end -}}
{{- $.Scratch.Get "index" | jsonify -}}
{{< /highlight >}}

I only want my search to look for blog posts, not every static page. To do this, I loop through my pages with the type "blog". Then, I create a dictionary which contains multiple key/value pairs of the data that I want. For instance, I want the title of my blog posts, so I create a key ("title") and a value (.Title). You can scroll through the code to get an idea of how to scrape other data (like a description, date, etc).


### Generating the JSON

After the template is created, just re-build the project. Doing this will create a JSON file, which will be used as our search index. In my case, I have a Hugo theme called "portio". So, to build my project, I run the command `hugo -t portio`. After running this command, I have a generated JSON file called `algolia.json` in my build (public) directory.

You can beautify this file and verify that all of the data is correctly collected. If data is null or not populated correctly, make some changes to `search-index.json`. Make sure that you're using the correct [Hugo variables](https://gohugo.io/variables/).


## Set up Algolia

Now, you can head over to the ALgolia interface to create a New Application (using the free plan). Then, within that New Application, create a New Index.

You'll have to jot down the Application ID, API key, and Index Name.

## Send Search Index to Algolia

Now that we have our search index file, we need to upload it to Algolia (so we can use their search algorithms). Using NPM, we have to install Algolia:

`npm install atomic-algolia --save`

Within your `package.json`, add a script called `algolia: atomic-algolia`.

If you run `npm run algolia`, it won't work because Algolia doesn't know which project you're uploading this search index to. To fix this, you'll need to run:

{{< highlight bash >}}
ALGOLIA_APP_ID={{ YOUR_APP_ID }} ALGOLIA_ADMIN_KEY={{ YOUR_ADMIN_KEY }} ALGOLIA_INDEX_NAME={{ YOUR_INDEX NAME }} ALGOLIA_INDEX_FILE={{ PATH/TO/algolia.json }} npm run algolia
{{< /highlight  >}}

Copy the values of your app id, api key, etc into these brackets. Now, when you run that command, you're search index will be uploaded to Algolia! Check the Algolia interface to make sure your data is present in that service. From the UI, you can configure, manage, and view analytics related to your index.

![Image](/images/blog/algolia-ui.png)

You can also search within the Algolia UI itself to see how your search will look on your website.
![Image](/images/blog/algolia-ui2.png)


## Displaying the Search Results

We're going to have to write some Javascript to interact with Algolia API's to interact with our search index. First, we'll have to import Algolia as a module. Easiest way to do this is by adding node modules, but I went with embedding the scripts directly (from a CDN).

To embed the modules via a CDN, I used JSDelivr, which is a large CDN for Javascript modules. Then I injected these scripts into my HTML:

{{< highlight html >}}
<script src="https://cdn.jsdelivr.net/npm/instantsearch.js@4.37.1"></script>
<script src="https://cdn.jsdelivr.net/npm/algoliasearch@4.11.0/dist/algoliasearch.umd.min.js"></script>

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/instantsearch.css@7.4.5/themes/satellite-min.css" integrity="sha256-TehzF/2QvNKhGQrrNpoOb2Ck4iGZ1J/DI4pkd2oUsBc=" crossorigin="anonymous">
{{< /highlight >}}

One of these is for a built-in theme, and the others are the modules to use Algolia search.

Now, create a `search.js` file which will interact with the Algolia API's to configure some things you'll need.

### Initialize Search

Start by initializing Search, by entering your index credentials.

{{< highlight js >}}
const search = instantsearch({
    indexName: 'your-index-name',
    routing: true,
    searchClient: algoliasearch(
        'your-app-id',
        'your-api-key'
    )
});
{{< /highlight >}}

### Display Results

Go to the HTML page you want your results to be displayed. Then create an empty div which will be where your results are shown:

`<div id="hits"></div>`

Back in the `search.js` file, we'll need to link that div to Algolia's API.

Algolia is built around widgets, one of which is the Hits widget which displays all of your data results. Configure your Hits widget with the below:

{{< highlight js >}}
search.addWidget(
    instantsearch.widgets.hits({
        container: '#hits',
        templates: {
            empty: '<h3 style="text-align: center;">No results found 😔. Search something else.</h3>'
        }
    })
);
{{< /highlight >}}

The container finds your HTML element which we defined in our HTML above. After it finds it, it will inject the widget into that HTML. 

An empty template field will display whenever the search results are not found.

To display the actual results, we'll need to add an item in our template:

{{< highlight js >}}
search.addWidget(
    instantsearch.widgets.hits({
        container: '#hits',
        templates: {
            empty: '<h3 style="text-align: center;">No results found 😔. Search something else.</h3>',
            item:
            `
            {{ range .Paginator.Pages }}
                <div class="image">
                    <img src="{{ image }}">
                </div>

                <div class="blog">
                    <span>{{ writtendate }}</span>
                    <h4>
                        <a href="{{ permalink }}">
                            {{#helpers.highlight}}
                                { "attribute": "title", "highlightedTagName": "mark" }
                            {{/helpers.highlight}}
                        </a>
                    </h4>
                    <h6>
                    [ {{tags}} ]
                    </h6>
                </div>
            {{ end }}
            {{ partial "pagination" .}}
            `
        }
    })
);
{{< /highlight >}}

Here, I'm looping through all of my pages, then displaying an image for each page, followed by the date that the blog was written, and the title of each blog.


### Search Bar

Results should be displayed now. Next, we'll add the search box which will filter our results.

In the HTML file, add the following div: 

`<div id="search-box"></div>`

Back in the `search.js` file, we'll initialize a search box widget:

{{< highlight js >}}
search.addWidget(
    instantsearch.widgets.searchBox({
        container: '#search-box',
        placeholder: "Search for articles",
        autofocus: true
    })
);
{{< /highlight >}}

Again, the container will look for the HTML element that you enter, and inject that widget into the HTML.


### Adding Other Widgets

As mentioned, Algolia has a [bunch of widgets](https://www.algolia.com/doc/guides/building-search-ui/widgets/showcase/js/) that you can configure. We've already added the Hits widget, which displays our results, and the Search Box widget, which displays a search box.

For my site, I also wanted categories/tags so that users can quickly sort an article by the category. I also wanted pagination below the results so users can navigate through my content.

Again, we need an empty div in our HTML. So for these, I will add the following in my HTML:

{{< highlight html >}}
<div id="menu"></div>
<div id="pagination"></div>
{{< /highlight >}}

For the categories/tags, you can use a Refinement List widget. But I went with the Menu widget which is pretty similar. Initialize it with:

{{< highlight js >}}
search.addWidget(
    instantsearch.widgets.menu({
        container: '#menu',
        attribute: 'tags',
        showMore: true,
        limit: 3,
        sortBy: ['count:desc']
    })
);
{{< /highlight >}}

Here, we are filtering by tags, which is a data attribute in my search index JSON. I also enabled a "Show More" button that shows all of my tags.

The Pagination widget was added like so:

{{< highlight js >}}
search.addWidget(
    instantsearch.widgets.pagination({
        container: '#pagination',
        scrollTo: false,
        showFirst: false,
        showLast: false,
        showPrevious: true
    })
);
{{< /highlight >}}

### Customizing Widgets

Finally, we've got a fully functioning Search. But the CSS may not look the way we want it to. You can customize the CSS by overriding the classes to your needs. Remember to test it out for both mobile and desktop devices!


## Finished!

Now, we've got a fully functioning Search on our Hugo site!


For more information:
- https://forestry.io/blog/search-with-algolia-in-hugo/

---
