---
title: "Hugo Extended on Netlify"
date: 2019-03-28T16:50:01+05:00
---

So I was setting up my website with Hugo and having hard time deploying in Netlify because of [various errors](https://github.com/gohugoio/hugo/issues/5745). I didn't want to struck with issue(s) so I switched my theme as I wanted my site to go live soon.

I picked [hugo-coder](https://github.com/luizdepra/hugo-coder/), it was great and similar to the previous theme [hello-friend-ng](https://github.com/rhazdon/hugo-theme-hello-friend-ng). I tweaked my [config.toml](https://github.com/rahilwazir/rahilw.dev/blob/master/config.toml) and pushed the changes, and ready to start the deployment.

Darn, again :worried: hit by an issue. It was related to SCSS compilation and Hugo uses `... | toCSS` pipe function for that, and it was not supported by regular Hugo version. I went to Netlify [build config](https://github.com/rahilwazir/rahilw.dev/blob/master/config.toml) and was trying to figure out, why is it not using the extended version or how can I force it to but no luck :thumbsdown:.

Found out :collision: the build image selection used by Netlify was **Ubuntu Trusty (14.04)** and there were some [missing dependencies](https://github.com/netlify/build-image/issues/183) in that image which was required by Hugo Extended version to work properly.

## The Solution :white_check_mark:

Go to **Deploy Settings - Build & Deploy - Continuous Deployment** and change your build image to **Ubuntu Xenial (16.04)**

![Netlify Build](/img/netlify-build.png)

Good luck :tada:
