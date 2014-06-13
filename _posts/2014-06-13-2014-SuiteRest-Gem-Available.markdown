---
layout: post
title:  "SuiteRest Gem Available"
date:   2014-06-13 13:00:00
categories: ruby netsuite
---

I've finally taken the time to clean up and open source some code I've been using internally for a while
to make interacting with NetSuite RESTlets less painful.

[SuiteRest](https://github.com/apbendi/suite_rest) is a simple Ruby Gem which lets you configure your NetSuite credentials, define a RESTlet
service you've deployed in NetSuite, and then call out to that service:

{% highlight ruby %}
SuiteRest.configure do |config|
	config.account    = 123456
	config.email      = "email@mail.com"
	config.role       = 1010
	config.signature  = "password"
end

get_world = SuiteRest::RestService.new( :type => :get,
					:script_id => 27,
					:deploy_id => 1,
					:args_def => [:world_description] )

get_world.call(:world_description => "Big") # "Hello Big World"
{% endhighlight %}

In the above example, I called out to a previously deployed RESTlet service in NetSuite
with the following code:

{% highlight javascript %}
function getTest(datain) {
	if(datain.worldDescription) {
		return("Hello " + datain.worldDescription + " World");
	} else {
		return("Hello World");
	}
}
{% endhighlight %}

If you're used to working with the developer friendly tools offered by most modern
SaaS providers, interacting and integrating with NetSuite can be a painful experience. This is one of a
handful of simple tools I've created to *slightly* improve the process which I'll be cleaning up and
open sourcing soon.

Check out [SuiteRest on GitHub](https://github.com/apbendi/suite_rest) if it would be useful to you.