---
layout: post
title: "Stick to Native"
categories: iOS design UI UX
---

Operating in the post-hype mobile era when most people don't use more than [a handful of apps][app count], developers are looking for every competitive edge they can find to appear on anyone's radar. The most recent one that popped up is released by a former Apple intern, the [Apollo Reddit client][apollo]. It received positive reviews on many tech blogs, praising one of its main value proposition: a Reddit client that feels very native to iOS. This somewhat validated, and revived, the ever more hazy concept that it is a good thing for mobile Apps to look and behave "natively". Even if we are to accept that as truth, these days one can still legitimately raise good questions about what that concretely means. Given the convergence of Android and iOS and the rise of React Native and Xamarin, where can we find the motivation to write the same feature twice in Swift and Kotlin? What is driving us to stick to the [Human Interface Guidelines][hig]? It really boils down to __maintainability__. We can dissect this by examining these two questions:

1. What constitutes native iOS?
1. Why is that _not_ good enough?

## What Constitutes Native iOS?
One obvious example is iOS stock apps. The model citizens of UIKit `Mail` and `Settings` effectively act as reference implementations of the [HIG][hig], demonstrating all the typical behaviours of iOS we are familiar with. However, it's easy to notice other Apple apps differ quite considerably. The `Weather` app features an unique layout, interaction, and presentation, unlike most others. There's also `Reminders` and `Notes`, which for some reason still retains the dotted texture background. `Music` and `Podcasts` app utilize that Now Playing bar which pulls up to a full playlist manager. `iMessage` has the extension bar at the bottom that enlarges upon interaction.

<div class="centered">
{% include thumbnailer.html img="native/reminder.jpeg" width="150px"%}
{% include thumbnailer.html img="native/weather.jpeg"  width="150px"%}
{% include thumbnailer.html img="native/itunes.jpeg"  width="150px"%}
</div>

While it's fair to say many stock apps have their own uniqueness, we can see they do have some characteristics that string them together. In particular, two things are worth noting:

1. Heavy reliance on tint colour and translucency.
1. Never unnecessarily introduces custom controls that aren't provided in UIKit.

Generally I find that if an app checks these two boxes, it will likely come across as native and familiar to iOS users. There are notable exceptions, such as Apple's `Clips` app, which draws heavy inspiration from `Snapchat`. But I categorize those apps a bit differently as their data is more media driven than text driven. My guess is that most developers have dragged standard UIKit elements into a Storyboard and produced an extremely natively (or boring) looking toy app at least once in their life. But at some point, they decided that isn't good enough. Why is that?

### Why Choose Brand Colour Over Translucency?
There is a very simple reason for why tint colour and translucency isn't appealing to developers, and that is branding. iOS navigation bar is developers' favourite place to show off their brands, mostly because that was what Apple taught everyone to do prior to iOS 7. This design tradition really stuck with the community and many apps aren't breaking free from that heritage. Big titles such as `Facebook`, `Quora`, `Twitch` and `Amazon` all feature solid navigation bar painted in their brand colour. Although some have started to move away, for instance `YouTube` and `Netflix` have both embraced the new style and removed their bright red.

<div class="centered">
{% include thumbnailer.html img="native/facebook.jpg" width="100px"%}
{% include thumbnailer.html img="native/quora.jpg" width="100px"%}
{% include thumbnailer.html img="native/twitch.jpg" width="100px"%}
{% include thumbnailer.html img="native/alexa.jpg" width="100px"%}
{% include thumbnailer.html img="native/old_youtube.png" width="200px"%}
{% include thumbnailer.html img="native/netflix.jpg" width="100px"%}
</div>

Branding choices are usually very intentional and subjective. Their presence (or lack of) affect users' perception of the product. A fairly recent survey conducted by The Verge showed some [60% of respondents did not know about Instagram's relationship with Facebook][verge]. In this case Facebook managed to create distinct perceptions of their products by lack of branding (on Instagram), probably a calculated choice. However, some other choices may appear more random. For instance, the `Gmail` app and some parts of the `Google Maps` app have the solid brand colour title bar, yet `YouTube` and `Google` app both tuned down on that dramatically. It's hard to say exactly what (if anything) is driving these decisions.

I recommend against the usage of brand colour backgrounds on iOS (tint colour is always okay). By using brand colours, we give up on one of the two properties we identified earlier that make an app feel native. Whether that price is worth the brand recognition is arguable in most cases. My belief is that most brands aren't strong enough for users to associate it with a particular colour. And if it is, then whether that extra branding is necessary becomes questionable. Essentially, the default case is that we probably don't need it. Special cases can always occur though, but that decision should be made carefully and on a case by case basis.

### Why Custom Controls?
There are some apps that really push the mobile UX forward. They often have one or two defining interactions not offered by UIKit that greatly complements the user experience. Not only do they serve as corner stone of the app, but they go much further and become highly influential in the industry. For example, `Instagram`'s double-tap, `Tinder`'s swipe-left, `Pinterest`'s flyout menu, and `Snapchat`'s fullscreen presentation. In the case of `Clear Todos`, its slide-to-complete gesture even got adopted by Apple and is now part of UIKit. 

<div class="centered">
{% include thumbnailer.html img="native/cleartodos.png"  width="150px"%}
</div>

These iconic custom controls are rare and far between. They are usually tailored to address a particular use case specific to that App. They exist to serve the user. However, we also see apps that let you do things that can be accomplished with UIKit, but for some reason are furnished with a complete suite of custom controls that basically offer the same UX experience as UIKit. This phenomenon appears to be quite common with banks, retailers, and news apps. It is generally a symptom of using third party libraries or development framework, pursuing the goal of reducing development effort, test set size, and unifying the app experience with Android. Unfortunately, this is almost always a bad thing for the end user.

## It's Not Worth It
One definitive disadvantage is giving up the other property that makes an app feel native. Except this time, the only reason is cost reduction. Depending on the framework in question, the experience can detract significantly from what iOS users expect. Badly implemented frameworks can also have significant impact on performance and stability, especially as iOS evolves and become backward incompatible with whichever iOS version the framework was last updated for. Modern write-once-deploy-everywhere solutions do a better job by essentially offering "super classes" of UIKit components at author time then compile down to native iOS code when built. But sometimes there is significant disjoint between the super classes for iOS and Android, one can legitimately ask, [why bother][xamarin]?

Another disadvantage that may or may not materialize is the accompanying risk of having code built entirely on third party frameworks. I am not against abstraction, but not all abstractions are equal. Using write-once-deploy-everywhere solutions top to bottom can lock developers in their ecosystem (and language), making switching back to native implementation prohibitively expensive. At that point, the product is stuck with it and is at the whims of the third party vendor. This was particularly hazardous during the earlier days of iOS where things moved rather fast. Even though things are a lot more stable now, mobile platform is still anything but stale. Proper architecture and abstraction can often alleviate this risk, but this extra level of concern adds to the complexity of projects, which doesn't help with reducing development time.

This is not to say code will magically stay up to date if developers choose to stick with native solution. Painful memories of ARC, auto layout, and Swift 3 transitions have probably scarred many iOS developers. But in the long run, these amortized efforts keep us away from irreversible technical debt. For the most part, Apple tries to make these transitions no more painful than they need to be. But their assistance generally only applies to developers who have been keeping their code up to date and native. As guests of UIKit, it is in developers' best interest to rely on UIKit API rather than third party support, so that when deprecation happens, we can leverage Apple's official guideline that often gives the most efficient migration path. Third party vendor can certainly do an excellent job of abstracting developers away from these system changes underneath, but again, that benefit is greatly reduce if the vendor becomes unable, or worse, unwilling to keep updating their framework. This will result in devastating consequence which often lead to significant rewrites of the application.

## Stay Native
If you can, stay native, because native _is_ the better choice for most of our needs.  If your App has an interaction UIKit can't satisfy, first evaluate whether the interaction is reasonable before dropping in a custom control. The occasional embedded web view can significantly reduce workload, and if done right it will blend in seamlessly. But venturing out of native development workflow should be carefully evaluated with its risks assessed. Do not carelessly and mindlessly walk off the beaten path.

[app count]: https://www.emarketer.com/Article/How-Many-Apps-Do-Smartphone-Owners-Use/1013309
[apollo]: https://apolloapp.io
[hig]: https://developer.apple.com/ios/human-interface-guidelines/overview/themes/
[youtube]: http://photos2.insidercdn.com/gallery/14490-10077-151005-YouTube-l.jpg
[verge]: https://www.theverge.com/2017/10/27/16552620/facebook-trust-survey-usage-popularity-fake-news
[xamarin]: https://developer.xamarin.com/api/root/MonoAndroid-lib/

<script src="{{site.baseurl}}/assets/thumbnailViewer.min.js"></script>
<link rel="stylesheet" href="{{site.baseurl}}/assets/thumbnailer.css">
