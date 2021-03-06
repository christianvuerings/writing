---
ID: 5559
post_title: 'Arrow functions are not the solution you&#8217;ve been looking for'
author: James DiGioia
post_excerpt: ""
layout: post
permalink: >
  https://jamesdigioia.com/arrow-functions-are-not-the-solution-youve-been-looking-for/
published: true
post_date: 2018-01-30 17:46:45
---
JavaScript's Arrow functions were supposed to solve all our `this`-related problems but instead just replaced those `this`-related problems with other `this`-related problems.

A friend of mine posted this in our local Slack channel, and I've seen a variation of this problem a number of times already:

[gistpen id="5562"]

Note the `<- Fails here`. Can you spot why? I'll wait...

Figure it out...

...yet?

Ok, I'll tell you. `this` inside of `listTables` is lexically-bound, so it's the same `this` as `foo`, _not_ the returned object. So if the function is called in global scope, which it likely is, `this === window`, or even `this === undefined`, depending on whether we're in strict mode.

We're just moving our problems around, and we're even getting to the point of introducing _more_ syntax to solve the problem arrow functions were supposed to solve in the first place (see the new class fields proposal, which will allow you to write this:

[gistpen id="5571"]

and the function stays bound to the class instance. None of this really solves the underlying problem, which is the repeated attempt to shoehorn patterns into the language that don't belong.

JavaScript is not a traditional class-oriented language. Stop trying to make it one.