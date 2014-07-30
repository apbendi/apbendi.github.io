---
layout: post
title:  "Web vs Mobile: A Night and Day Difference"
date:   2014-07-29 23:00:00
categories: web javascript react mobile ios objective-c swift
---

For the last couple weeks at my *day* job, I've been building a simple single window javascript web app- an internal tool for cleaning, tagging, and maintaining our CRM data. At *night* I've been spending bits and pieces of free time getting better at iOS development by building a couple of native apps.<sup>1</sup> Appropriately, the difference between the two experiences has been night and day. (See what I did there?)

Countless keystrokes have been spent on the web vs. native for mobile debate, so I won't bother beating the dead [Horse JS](http://twitter.com/horse_js). But I will simply add my two cents: philosophical open vs. closed debates aside, the developer experience is simply leaps and bounds better in native iOS.<sup>2</sup>

On the web, the frontend toolchain is a hot mess. Node + npm + grunt + gulp + bower + requirejs + jasmine + mocha + html + haml + yaml + css + less + sass + jquery +.....I've only scratched the surface, and we haven't even picked a JavaScript framework yet!<sup>3</sup>

XCode has its quirks and limitations, for sure, but at the end of the day you really just open it up and, well, code. Compared to the nightmare of constantly fiddling with all of the above, it's frankly a dream come true.

We have all these layers and hacks on top of hacks because web technologies don't actually make any sense. Building apps in HTML, CSS, and JavaScript isn't just less than ideal, its borderline **insane**. We only accept the insanity because we're used to it, and we can't ditch these tools because, well...we'd break the Internet.

So is there any hope for less painful development on the web, or are we doomed to gimp forward with hacks and kludges while native mobile development gets cool new toys likes Swift?<sup>4</sup> A few months ago I tweeted something half jokingly, but increasingly I think this really is the future:

<center>
	<blockquote class="twitter-tweet" lang="en"><p>At what point do we just start calling pure <a href="https://twitter.com/hashtag/JavaScript?src=hash">#JavaScript</a> &#39;browser bytecode&#39;?</p>&mdash; Ben DiFrancesco (@BenDiFrancesco) <a href="https://twitter.com/BenDiFrancesco/statuses/460169194106286080">April 26, 2014</a></blockquote>
	<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
</center>

NOW is the time to start treating JavaScript like browser bytecode. Languages like ClojureScript are well on the way to making this a reality. New entrants like [Elm](http://elm-lang.org/) take the idea a step further compiling down not just to JavaScript, but to HTML and CSS as well, meaning you can write front end "web apps" without a single webby-feeling technology.

The future of web development is not a better markup language or another testing framework or a package manager you install with a package manager<sup>5</sup> or a dynamic stylesheet language. And it's definitely not yet another MVC JavaScript framework. These tools pale in comparison to the ever-improving counterparts on mobile, and developers will rightly shun the former for the latter.

If web development has a future it has to be this: sane, modern languages compiling down to web-stuff underneath.

---------
<small>
<sup>1</sup> One of which I just submitted for review to the App Store, fingers crossed!
</small>

<small>
<sup>2</sup> Having done almost no Android development to date, I can't speak to what its like on that platform. I've heard its rough around the edges, but has made some big strides recently.
</small>

<small>
<sup>3</sup> For the record, I'm using React, which I actually really like and think brings a number of super smart and important ideas to the table.
</small>

<small>
<sup>4</sup> And one day, one would assume, Go on Android.
</small>

<small>
<sup>5</sup> npm install -g bower
</small>