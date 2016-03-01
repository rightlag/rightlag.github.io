---
layout:     post
title:      pyswagger - create Python HTTP clients via JSON formatted Swagger schemas
date:       2016-02-29 15:50:00
summary:    pyswagger allows developers to load JSON formatted Swagger schemas and issue requests to the endpoints defined in the schema.
categories: python swagger open API
---

A project that I've been working on recently is [https://github.com/rightlag/pyswagger](pyswagger). The purpose of `pyswagger` is to load any JSON formatted [http://swagger.io/](Swagger) schema and generate an abstract client to issue requests to the [http://swagger.io/specification/#pathsObject](paths) defined in the schema. This project has proven to be challenging but fun at the same time. I'd like to talk about why I decided to write `pyswagger` and talk about some of the issues I faced while writing it.

### Why did I write it?

For a while now, I've been writing Python modules that interface with HTTP APIs. While this is great, it becomes redundant. I think one of the things that really resonated with me was the talk given by Raymond Hettinger at [https://www.youtube.com/watch?v=wf-BqAjZb8M](PyCon 2015). While the talk mostly focuses on writing intelligible code, he mentions the use of creating a template for additional projects in the foreseeable future. This just made sense to me. I asked myself, "Why do I keep rewriting the same code?" Almost all of the modules that I've written that work with HTTP APIs have the same structure.

So, after doing some research, I found out about [http://swagger.io/](Swagger). I thought, "Perfect, this is exactly what I need." So, I started to write a module that would read the schema definitions and create an abstract client for issuing requests.

### Challenges

**Make it intelligible**

When I write Python code, I tend to think. *A lot*. I like to make sure that my code is, as Raymond mentioned, intelligible. I want to make sure that if other developers decide to contribute to my code, they can do so at ease. Or, even if they don't decide to contribute, but are reading through it, be able to easily read the code.

**Make it automated**

What do I mean by this? I wanted to make the client "smart". For instance, in Swagger definitions, the `consumes` key is a list of valid MIME types when issuing requests. So, I wanted the client to automatically determine the `Content-Type` to be used if the user does not specify. This prevents the amount of code that the developer needs to write when using `pyswagger`. After all, less is more.

**Maintainability**

A lot of open source projects that I see on GitHub eventually go unmaintained. I didn't want that to happen to `pyswagger`. Instead, I want to keep maintaining it. I know the code isn't perfect, and I'm sure other developers could identify some code that I could clean up or make better. Not to mention, I haven't covered all of the features that Swagger offers.

### Future thoughts

I'd like to add more support for `pyswagger`. I think the project has potential and could be used for a variety of purposes. I'd like to implement support for loading Swagger schemas directly as file pointers as well as reading them from websites. I'd also like to support validation when issuing requests. This would be accomplished by reading the models defined in the Swagger schema and identifying the data types of the model and validating them against user input.

Overall, this has been a fun project to work on. I'm glad that I decided to give it a go. It's kept me busy and also adds another project to my GitHub repository.

If you want to contribute to `pyswagger`, please, by all means, do so:

[https://github.com/rightlag/pyswagger](https://github.com/rightlag/pyswagger)
