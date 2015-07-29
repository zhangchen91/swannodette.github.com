---
layout: post
title: "ClojureScript Next"
description: ""
category: 
tags: []
---
{% include JB/setup %}

<link href="/assets/css/codemirror.css" rel="stylesheet"></link>
<link href="/assets/css/cljs-next/main.css" rel="stylesheet"></link>

## Clojurescript 1.7

Yes, at long last ClojureScript has a version number. Enthusiastic
users have often asked *How long till 1.0?*. However 1.0 would not
correctly reflect the time, effort, and feature set that comes with
four years of very active development. Instead we're adopting 1.7 as
this communicates the incredibly important relationship that
ClojureScript has with its parent language Clojure.

One the biggest aspect of this relationship - the differences between
Clojure and ClojureScript are quite small. So much so that with the
help of reader conditionals, a port of tools.reader, and some
dedicated effort over the past two months, ClojureScript can now
compile itself.

## Our Old Friend, Eval

Let's cut to the chase. The following is a simple ClojureScript
program that creates a definition and immediately invoke it. Click
the **EVAL** button.

<div class="eval-cljs">
    <textarea id="ex0" class="code"></textarea>
    <div class="eval-ctrl">
        <input id="ex0-out" type="text"></input>
        <button id="ex0-run" class="eval">EVAL</button>
    </div>
</div>

<script type="text/javascript"
src="/assets/js/cljs_next/main.js"></script>

The humble result hides the enormity of the event :)

We read a string out of [CodeMirror](https://codemirror.net/), read
with [tools.reader](https://github.com/clojure/tools.reader) into a
persistent data structure, passed it into the ClojureScript analyzer,
constructed an immutable AST, passed that to the compiler, and
generated JavaScript with inline source maps. All of this happened
inside of your web browser.

To be very clear, *this precisely the same compiler that runs
on the Java Virtual Machine running on Plain Old JavaScript*.

For the unbelievers, open Chrome DevTools, open the Sources tab and
you should see something like the following:

<img width="590" style="border: 1px solid #ccc" src="/assets/images/inline_source_maps.png" />