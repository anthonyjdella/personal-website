---
title: LinkedIn to JSON Chrome Extension
date: 2021-10-10T12:49:27.000+06:00
thumbnail: ../images/portfolio/extension.png
service: Chrome Extension, Javascript, JSON
client: Myself
shortDescription: I updated an existing Chrome Extension which collects data from your LinkedIn profile and exports it into JSON, which can be used with the JSON Resume standard.
challenge: JSON Resume is a standardized JSON-based resume. Someone created an open-source Chrome Extension that looks at your LinkedIn profile and exports the data into JSON. However, this tool was not updated with the most recent JSON Resume Schema, and also did not work with my customized schema.
solution: Since I created my own JSON Resume schema, I wanted it to work with this tool. So, I added functionality to use my custom schema, as well as v1 of the JSON Resume project.

---

[LinkedIn to JSON Resume](https://github.com/joshuatz/linkedin-to-jsonresume) is a Chrome Extension that fetches data from your LinkedIn profile and exports the data into JSON. This JSON can then be used with the [JSON Resume Schema](https://github.com/jsonresume/resume-schema). I use LinkedIn a lot and thought that this tool would be a great way to have a ['single source of truth'](https://en.wikipedia.org/wiki/Single_source_of_truth). So with this, if I keep my LinkedIn up to date, I won't need to manage a resume or JSON file. 

`In the past, I found it annoying to have to update both a resume and LinkedIn, but with this, I only need to update my LinkedIn!`

However, there were some issues with this project.

1. It was outdated and used an old version of the JSON Schema.
2. The exported JSON had to be based on the supported schema definition.

Therefore, I updated it to accept the newest JSON schema definition (version 1.0.0) and added support for my customized JSON schema. I created my own schema, so that I could use custom fields for my JSON resume.

After adding these features, all I have to do is add build the project and add the Extension to my Chrome browser. Then, when I visit a LinkedIn profile, I can easily export that profile into a JSON file.

![Firebase](/images/portfolio/linkedin.png)
Here, you can see the Chrome Extension in use, when visiting a LinkedIn profile.