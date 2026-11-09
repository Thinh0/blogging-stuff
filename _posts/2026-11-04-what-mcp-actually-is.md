---
layout: post
title: "What MCP actually is"
subtitle: "The protocol that lets AI apps talk to everything else"
categories: [tech]
---

Lately i keep seeing "MCP" everywhere. In AI tools, in settings menus, in people's posts about what their assistant can do now. I nodded along for a while like i knew what it meant, but honestly i didn't. I only knew it had something to do with letting an AI use other apps. So what is MCP really? Why did it become such a big deal so fast, even companies that compete with each other seem to be using it? And is it safe to let an AI plug into all my stuff like that?

## So what is MCP?

MCP stands for "Model Context Protocol". Anthropic, the company behind Claude, put it out in November 2024. A "protocol" is just an agreed set of rules for how two things talk to each other, kind of like how every phone charger would be a mess if each phone brand picked its own plug. Before MCP, if you wanted an AI app to use something like your calendar or your files, someone had to build a custom connection just for that one app and that one tool. With MCP, a tool gets set up once, and any AI app that speaks MCP can use it. That's the idea, anyway. I'm still figuring out how well it works in real life.[^wiki]

## Wait, isn't that just an API?

That was my first thought too. An API is how one program asks another program to do something, like a weather app asking a weather service for today's forecast. The catch is that every API is a little different: its own addresses, its own format, its own rules, and the instructions are written for human developers to read. MCP doesn't replace APIs. It sits on top of them. An MCP server usually wraps an API that already exists and describes it in one standard way: here's what I can do, here's what each thing is for, here's what you need to give me. Because everything is described the same way, an AI can look at the list and figure out how to use it, without someone writing special code for every single service. So the way I'd put it is that an API is how the tool works, and MCP is a common way to introduce that tool to an AI. That's my own summary, so I'll want to double check it against the docs as I keep reading.


## References

[^wiki]: [Model Context Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol) (Wikipedia), which describes it as an open standard for connecting external tools and resources to AI apps, and [MCP joins the Agentic AI Foundation](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/) (MCP blog). The phone charger comparison is mine, not from either source.
