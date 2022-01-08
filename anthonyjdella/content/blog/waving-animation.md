---
title: "How to Animate an Emoji with CSS"
date: 2021-12-01T12:49:27+06:00
writtenDate: "December 1, 2021"
authors: "Anthony Dellavecchia"
featureImage: images/blog/wave-emoji.png
postImage: images/blog/wave-emoji.png
tags: ["css", "animation", "front-end", "how-to"]
---

If you go to the home page of [this website](https://anthonydellavecchia.com), you might find some hidden "easter eggs" around the page. One of which is an emoji that is animated using CSS. 👋 is the emoji. It's just a waving hand, that doesn't actually wave. There is no animation, so I wanted to make it move. It's actually pretty easy!

### Step 1: Create HTML

{{< highlight html >}}
    <div class="waving" data-hover="👋">
        Hi
    </div>
{{< /highlight  >}}

All I've done here is create a simple div with the text, "Hi". Then I've given it 2 HTML attributes, `class` and `data-hover`. The contents within `data-hover` ( 👋 ) is what will be animated.

### Step 2: Create CSS

{{< highlight css >}}

.waving:before {
  content: attr(data-hover);
}

.waving:hover {
  animation-name: wave-animation;
  animation-duration: 3.0s;
  animation-iteration-count: infinite;
  transform-origin: 70% 70%;
}

@keyframes wave-animation {
  0% {
      transform: rotate( 0.0deg)
  }
  10% {
      transform: rotate(14.0deg)
  }
  20% {
      transform: rotate(-8.0deg)
  }
  30% {
      transform: rotate(14.0deg)
  }
  40% {
      transform: rotate(-4.0deg)
  }
  50% {
      transform: rotate(10.0deg)
  }
  60% {
      transform: rotate( 0.0deg)
  }
  100% {
      transform: rotate( 0.0deg)
  }
}
{{< /highlight  >}}

`.waving:before` defines the content of which is to be displayed ( 👋 ).

`.waving:hover` defines what action happens when we hover over that element. In this case we have an `animation-name` which is defined below in `@keyframes wave-animation`. We also give it an animation-duration of `3 seconds` and tell it to `animate infinitely`.

`@keyframes wave-animation` is where we create the actual animation. In this case, I wanted to make the hand wave, so to do this I just want the hand to rotate back and forth. I add different keyframes and tell it to rotate a certain number of degrees in certain intervals. This mimics 👋 actually waving!

You can apply this basic template to any emoji. Be creative! For example, you can try to animate a rocket 🚀 using CSS. Just think of what type of animation you want it to do (possibly translate up and down).
