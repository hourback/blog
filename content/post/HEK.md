+++
date = "2015-07-13T18:21:48-05:00"
draft = false
title = "Heka + Elasticsearch + Kibana = HEK"
tags = [ "elasticsearch", "heka", "kibana", "logging" ]
categories = [ "logging" ]
+++
I'm working on getting all of these working together.

I had to write a custom Lua decoder to parse the funny time stamps in our WebSphere logs.

At one point, the time stamp from WebSphere was being copied to another field, converted to nanoseconds, and sent to Elasticsearch as some kind of integer. I was getting errors from Kibana and Elasticsearch about running out of heap space, but googling this led to no conclusive answer. Only by determining that the Heka payload I was sending to Elasticsearch is what was causing the crash did I start narrowing it down to a particular Heka message field.
