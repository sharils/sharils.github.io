---
layout: post
title:  "Postman v.s. SuperTest"
date:   2018-12-23 23:38:15
categories: jekyll update
---

TL;DR

I decided to use Postman + Newman whenever I think of SuperTest.

[Postman][1] and [SuperTest][2] are both tools for integration tests at the HTTP API
level. And with [Newman][3], we can turn run Postman tests from CLI. This makes
them close matches.

[1]: https://www.getpostman.com/ "Postman | API Development Environment"
[2]: https://github.com/visionmedia/supertest "visionmedia/supertest: Super-agent driven library for testing node.js HTTP servers using a fluent API"
[3]: https://github.com/postmanlabs/newman "postmanlabs/newman: Newman is a command-line collection runner for Postman"

## Benefits

Below are reasons I decided to use Postman.

### Language Agnostic

Postman is language agnostic. In other words, you can switch the application
under test (AUT) from one language to another while still keeping some tests.
Assume you decide the rewrite a PHP service in Elixir then all your existing
Postman tests against the PHP version is not wasted.

### Unclosed Handles Won't Block

mocha / jest (I suspect jasmine too) hangs with unclosed handles. This happens
especially when Koa is used with SuperTest, unless you do research and figure
out that you have to pass `app.callback()` to SuperTest and you might need to
check module.parent to ensure that you don't run `app.listen()` when it's
imported by a test. One might argue that resources should be properly shutdown
anyway. What is totaly right. But whether resources are shutdown properly
shouldn't be a blocker to write tests for your app.

### Easy To Learn

Postman has GUI and it's straight forward, I'll consider it easier to learn. We
can hire interns to do API testing with very little training. While with
SuperTest, we'll have to train our inters to write proper JavaScript. One might
argue that we also need to train interns to write Postman script. Sure, but
right in the script panel, there is already a list of common tests available
there.

### cURL Imports

Postman allows one to import tests written in cURL this greatly reduce the
amount of time required to write test for legacy system. You just open the
Network tab in any developer tool and click copy as curl then import it into
Postman. Done.

### Demo Playground

Postman is also a good tool for doing step by step demos. While in supertest,
all those steps are combined and become just one green check. Not to mention
how easy it is for one playaround with it.

## Drawbacks

Of course there are drawbacks:

### Code Reuse

There is not easy way to reuse a request, you can only duplicate. Then you have
maintenance issue.

### SCM Diff

Git diff between Postman collection is harder to understand than supertest.

### Weird TDD

You can still do TDD with Postman, but it becomes weird because you no longer
"write" tests. That's weird feeling to do that.

### SSL CA Support

Postman doesn't allow one to add a trusted CA yet. And there is an [open
issue][4] for that. This is a blocker for testing new HTML5 features on
localhost that requires SSL connection on the server side. E.g. U2F support.

[4]: https://github.com/postmanlabs/postman-app-support/issues/3152 "[Feature Request] Add Root and Intermediary CA · Issue #3152 · postmanlabs/postman-app-support"

### Swagger Support

Postman doesn't correctly import Swagger files. If you copy and paste the
example Swagger Petstore swagger file, and import it into Postman. You will
find that the body of the `PUT /pet` command is showing the description from
the same method of on Swagger. `PUT` is not the only method that is broken,
it's every method with body that's broken.

### Enable/Disable Tests

It's impossible to enable or disable a test now.

### Blacklist/Whitelist Tests

It's impossible tag tests and include/exclude tests based on the tags. E.g.
tests that integrates with the real 3rd party API instead of mocks.

## Bonus

One might be wondering the difference between Postman and Insomnia. My answer
is that Postman allow you to run tests from CLI, while Insomnia supports
Swagger correctly.
