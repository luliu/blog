---
layout: post
title: "The Apollo iOS Reddit Client"
categories: iOS design UI UX
---

<script src="{{site.baseurl}}/assets/thumbnailViewer.min.js"></script>
<link rel="stylesheet" href="{{site.baseurl}}/assets/thumbnailer.css">

A former Apple intern released the [Apollo Reddit client][apollo]. Various tech blogs gave positive reviews of the app, praising its main value proposition: it feels extremely native to iOS. After using it for a few days, I agree, the app blends very nicely with iOS stock apps. But why is this news worthy? Is it abnormal for an app to use and feel native to the iOS platform? Or did this app push the boundary of third party "native-ness"? Are apps like this actually so few and far between? If so, what is motivating developers to venture outside of [Human Interface Guidelines][hig] and what's provided in UIKit? Is there anything wrong with being "standard"?

All of these questions fundamentally boil down to two things:

1. What constitutes native iOS?
1. Why is that _not_ good enough?

### What Constitutes Native iOS?
One obvious benchmark is iOS stock apps. The model citizens of UIKit `Mail` and `Settings` affectively act as sample implementations of the HIGS, demonstrating all the typical behaviours of iOS we are familiar with. However, it's easy to notice other Apple apps can differ quite considerably. The `Weather` app features an unique layout, interaction, and presentation, unlike most others. There's also `Reminders` and `Notes`, which for some reason still retains the dotted texture background. `Music` and `Podcasts` app utilize that Now Playing bar which pulls up to a full playlist manager. `iMessage` has the extension bar at the bottom that enlarges upon interaction.

<div class="centered">
{% include thumbnailer.html img="reminder.jpeg" width="150px"%}
{% include thumbnailer.html img="weather.jpeg"  width="150px"%}
{% include thumbnailer.html img="itunes.jpeg"  width="150px"%}
</div>

So it's fair to say many stock apps have their own uniqueness, some hardly have much similarity with others. However, I noticed they share at least two things in common:


1. Heavy reliance on tint colour and translucency.
1. Never unnecessarily introduces controls that aren't provided in UIKit.

### Why Is That Not Good Enough?

- The value of simple


[apollo]: https://apolloapp.io
[hig]: https://developer.apple.com/ios/human-interface-guidelines/overview/themes/
