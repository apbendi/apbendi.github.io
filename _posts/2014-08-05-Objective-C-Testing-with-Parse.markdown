---
layout: post
title:  "Objective-C Testing with Parse"
date:   2014-08-05 23:00:00
categories: mobile ios objective-c
---

I recently released my first app to the [app store](https://itunes.apple.com/us/app/real-rosary/id887065541?ls=1&mt=8). This was a simple app a great way to get my feet wet with Objective-C and Cocoa. I'm already working on my next side project, and this one is significantly more complicated and includes a [Parse](https://parse.com/) backend for syncing data.

With a proof-of-concept of the app already working, I decided that I've been putting off learning unit testing in Objective-C long enough. I've also resolved to take a TDD approach for adding features to the app moving forward.

Clearly, reading/writing data from Parse as part of my tests is not a viable option for a number of reasons, slow test performance and junk tset data being top among them. I knew I needed to mock & stub my way around the network calls like I've done with asynchronous calls in Ruby, but it took quite a bit of fumbling around to get that all working. Here are a few tips that might help you if you're going down the same path.

You'll want to use [OCMock](http://ocmock.org/). There's some serious Objective-C magic going on behind the scenes to make this library work, but luckily we don't have to understand it to get it working. Once this library is set up, you'll be able to write specs and mocks in a way similar to RSpec (in Ruby) or Jasmine (in Javascript).

Follow the instructions [here](http://ocmock.org/ios/) to get the library working with your project, with a couple of caveats:
	
1. Don't actually create the usr/lib and usr/include "folders" within XCode, as the screenshots suggest. If you clone the [example project](https://github.com/erikdoe/ocmock/tree/master/Examples/iOS7Example) it's obvious these should actually be created **on the filesystem**, despite what the screenshot show.
2. Don't set the `-ObjC` linker flag. If you do this with the Parse framework included, it will try to force links with other libraries included within Parse, specifically the Facebook authentication libraries. Instead, set `-force_load $(PROJECT_DIR)/usr/lib/libOCMock.a` (assuming you used the suggested paths from the intstructions).

Now time for some concrete examples of using mocks to run tests on objects back by Parse. Do you have objects that extend `PFObject` to add additional functionality? This a great way to integrate with Parse while keeping your design clean, but how do we test these objects and run tests that interact with them?

You'll want to use a partial mock for this, creating a 'real' instance of the object and then use mocks or expectations to prevent/verify calls to network functions:

{% highlight objc %}
MyObject *object = [[MyObject alloc] initWithProperty:property];
id objectMock = OCMPartialMock(object);

OCMExpect([objectMock save]);
/*
DO TEST THINGS WITH THE OBJECT, TRIGGERING A SAVE
....
*/
OCMVerifyAll(objectMock);
{% endhighlight %}

Finally, how do we perform a "query" without actually performing the operation, while at the same time returning some fake test data from the would-be-callback. First, use expectations to capture/verify building the criteria of the query, then delgate to a block to capture the callback and provide your test data:

