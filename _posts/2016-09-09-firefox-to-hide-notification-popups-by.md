---
title: 'Firefox to hide notification popups by default starting next year'
date: 2019-11-03T02:57:00+01:00
draft: false
---

![Firefox Push Notification Permission Request](https://zdnet1.cbsistatic.com/hub/i/2019/04/02/cb03c423-35d5-4fdc-8da1-8c3d6da17f98/44f3e20250a8f8f1c92da9ddcb3de0b3/push-notification-request.jpg)

In a move to fight spam and improve the health of the web, Firefox will hide those annoying notification popups by default starting next year, with the release of Firefox 72, in January 2020, ZDNet has learned from a Mozilla engineer.

The move comes [after Mozilla ran an experiment back in April](https://www.zdnet.com/article/firefox-to-run-experiment-to-reduce-push-notification-permission-spam/) this year to see how users interacted with notifications, and also looked at different ways of blocking notifications from being too intrusive.

Usage stats showed that the vast majority (97%) of Firefox users dismissed notifications, or chose to block a website from showing notifications at all.

As a result, Mozilla engineers have decided to hide the notification popup that drops down from Firefox's URL bar, starting with Firefox 72.

If a website shows a notification, the popup will be hidden by default, and an icon added to the URL bar instead. Firefox will then animate the icon using a wiggle effect to let the user know there's a notification subscription popup available, but the popup won't be displayed until the user clicks the icon. We've recorded a GIF of this new routine, [here](https://imgur.com/fN1JIg3).

Firefox Nightly versions already come with this notification popup blocker active, but the stable Firefox branch is scheduled to get it next January.

### The Notification API, and how it all went south

Notification popups were added to modern browsers in Chrome 22 (September 2012) and Firefox 22 (June 2013), with the addition of the Notifications API.

Their initial purpose was to allow websites to display notifications, and alert users of new content, after users closed a website's tab.

For example, you subscribed to Slack notifications, have a conversation, and close the Slack browser tab. The Notifications API allowed websites to show a popup when you received a new message, or there was new content available in your (now-closed) Slack tab.

News sites, such as ZDNet, also use notifications to alert users when new articles are out. Social networks and instant messaging clients use it to show alerts for trending topics or new messages.

The feature has its use cases, and can be extremely useful, but only when used by legitimate organizations.

### Fraudsters and spammers love notifications  

But over the past few years, unscrupulous groups have realized that the Notifications API provides an ideal method of pushing spam to users, even after users left the malicious site.

![shady-site.jpg](https://www.zdnet.com/article/firefox-to-hide-notification-popups-by-default-starting-next-year/#ftag=RSSbaffb68)

<span><img src="https://zdnet2.cbsistatic.com/hub/i/r/2019/11/03/fa4eebd1-c62e-45e8-b586-6120cf0d5bdc/resize/370xauto/14fc1f82f502f1e9dbf7a0b880878747/shady-site.jpg" alt="shady-site.jpg" /></span>

Image: Jerome Segura

Cybercrime groups have been luring users on random sites, and showing notification popups. If users accidentally clicked on the wrong button and subscribed to one of these shady sites, then they'd be pestered with all sorts of nasty popups.

Malicious threat actors have been seen using notifications (also known as subscription spam) to push links to shady products, links to malware downloads, or run-of-the-mill pill or Viagra spam \[[1](https://www.bleepingcomputer.com/news/security/forget-email-web-sites-use-notifications-to-spam-your-browser-instead/), [2](https://www.bleepingcomputer.com/news/security/sites-trick-users-into-subscribing-to-browser-notification-spam/)\].

"Notification spam is quite common, especially via certain types of publishers and malvertising in general," Jérôme Segura, malware analyst at Malwarebytes, told _ZDNet_ in an interview today.

"Since most browsers can block ad popups or popunders, push notifications have been greatly abused," Segura added. "In fact, I even question the merits of such a 'feature' in the first place or at least some serious oversight in how it could be implemented.

"Years ago, people would come to you about annoying ad notifications popping up on their machine, and that was usually due to adware programs \[installed locally\]. But these days, I would say this has been largely replaced by notification spam, which is very easy to fall for with some basic social engineering," he added.

"In comparison to cleaning up an infected machine, it's actually much easier to remove already allowed notifications, but most people just don't know how," Segura said.

And browser makers, too, have realized that the feature can be quite annoying, and downright dangerous. In recent years, most browsers have added settings to block websites from showing notifications.

However, Mozilla is the first browser vendor to block notification popups by default.

"I think Mozilla's decision is good for the health of the web," Segura told _ZDNet_.

_You can unsubscribe from receiving notifications from sites via any browser's settings section. Most browsers support a search feature in the settings section. Users can use it to search for the "notifications" options and block or unsubscribe from the shady sites._

![firefox-notifications-settings-2.png](https://www.zdnet.com/article/firefox-to-hide-notification-popups-by-default-starting-next-year/#ftag=RSSbaffb68)

<span><img src="https://zdnet3.cbsistatic.com/hub/i/2019/11/03/5ea99d42-0e2d-4b8e-88db-52c1c4e8b3e8/1c3fe089584a790a60d11b8998460151/firefox-notifications-settings-2.png" alt="firefox-notifications-settings-2.png" /></span>

  
  
from Latest Topic for ZDNet in... https://ift.tt/32a3qnR