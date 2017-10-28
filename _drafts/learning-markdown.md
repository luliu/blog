---
layout: post
title: "The Apollo iOS Reddit Client"
categories: iOS design UI UX
---

A former Apple intern released the [Apollo Reddit client][apollo]. Various tech blogs gave positive reviews of the app, praising its main value proposition: it feels extremely native to iOS. After using it for a few days, I agree, the app blends very nicely with iOS stock apps. But why is this news worthy? Is it abnormal for an app to use and feel native to the iOS platform? Or did this app push the boundary of third party "native-ness"? Are apps like this actually so few and far between? If so, what is motivating developers to venture outside of [Human Interface Guidelines][hig] and what's provided in UIKit? Is there anything wrong with being "standard"?

All of these questions fundamentally boil down to two things:

1. What constitutes native iOS?
1. Why is that _not_ good enough?

### What Constitutes Native iOS?
One obvious benchmark is iOS stock apps. The model citizens of UIKit `Mail` and `Settings` affectively act as sample implementations of the HIGS, demonstrating all the typical behaviours of iOS we are familiar with. However, it's easy to notice other Apple apps differ quite considerably. The `Weather` app features an unique layout, interaction, and presentation, unlike most others. There's also `Reminders` and `Notes`, which for some reason still retains the dotted texture background. `Music` and `Podcasts` app utilize that Now Playing bar which pulls up to a full playlist manager. `iMessage` has the extension bar at the bottom that enlarges upon interaction.

<div class="centered">
{% include thumbnailer.html img="reminder.jpeg" width="150px"%}
{% include thumbnailer.html img="weather.jpeg"  width="150px"%}
{% include thumbnailer.html img="itunes.jpeg"  width="150px"%}
</div>

So it's fair to say many stock apps have their own uniqueness, some hardly have much similarity with others. However, I noticed they do share some characteristics that string them together. In particular, two things are worth noting:

1. Heavy reliance on tint colour and translucency.
1. Never unnecessarily introduces controls that aren't provided in UIKit.

Generally I find that if an app checks these two boxes, it will likely come across as native and familiar to iOS users. It will be your typical iOS app so to speak. There are notable exceptions, such as Apple's `Clips` app, which draw heavy inspiration from `Snapchat`. But I interpret those apps a bit differently as their data is more image driven than text driven. Now that we have identified what constitutes native iOS, we are ready to tackle the next question.

### Why Is That Not Good Enough?
There is a very simple reason for why tint colour and translucency isn't appealing to developers, and that is branding. iOS navigation bar is developers' favourite place to put their brand colour and logo, mostly because that was what Apple taught everyone to do prior to iOS 7. This tradition has really stuck with the community and many apps aren't breaking free from that heritage, `Facebook` and `Quora` sprint to mind. `YouTube` just recently parted from their [giant red banner][youtube].


[apollo]: https://apolloapp.io
[hig]: https://developer.apple.com/ios/human-interface-guidelines/overview/themes/
[youtube]: http://photos2.insidercdn.com/gallery/14490-10077-151005-YouTube-l.jpg

<script src="{{site.baseurl}}/assets/thumbnailViewer.min.js"></script>
<link rel="stylesheet" href="{{site.baseurl}}/assets/thumbnailer.css">
