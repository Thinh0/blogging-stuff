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

## Why did everyone jump on it?

This is the part that surprised me. Right after it came out, a lot of people figured it would be one more standard that nobody uses. Instead, companies that normally compete with each other got on board. OpenAI, which makes ChatGPT, added support for it, and Google and Microsoft did too, though I couldn't find clear dates for all of them.[^adopt] Then in December 2025, Anthropic gave MCP away to a group under the Linux Foundation (a non-profit that looks after a lot of open source projects). The group is called the Agentic AI Foundation, and Anthropic started it together with Block and OpenAI, with Google, Microsoft, Amazon, Cloudflare and Bloomberg backing it. The point was that no single company owns the rules anymore.[^aaif] My guess for why it spread so fast is that everyone had the same headache of building one-off connections, and a shared plug is easier than fighting over whose plug to use. But that's just my guess.

## Is it safe?

Not automatically, and this is the part that made me slow down. Once an AI can use your tools, the risks come from what it reads and what it's allowed to touch. One is "prompt injection": someone hides instructions inside something the AI reads, like a web page or a GitHub issue, and the AI treats those instructions as if you wrote them. Another is "tool poisoning", where the bad instructions are hidden in the description of the tool itself, which the AI reads in full even though you never see it. There's also the "rug pull": a tool looks fine when you approve it, then quietly changes later. And if a tool gets more access than it needs, like your whole drive when it only needs one folder, any mistake gets bigger.[^risk] The advice I kept seeing is pretty down to earth: only use tools from sources you trust, give them the smallest access possible, and treat anything a tool sends back as untrusted. Some of the sources selling fixes are companies that sell security products, so I'm taking their warnings seriously and their pitches with a grain of salt.

## References

[^wiki]: [Model Context Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol) (Wikipedia), which describes it as an open standard for connecting external tools and resources to AI apps, and [MCP joins the Agentic AI Foundation](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/) (MCP blog). The phone charger comparison is mine, not from either source.
[^adopt]: [A Year of MCP: From Internal Experiment to Industry Standard](https://www.pento.ai/blog/a-year-of-mcp-2025-review) (Pento), [MCP Enterprise Adoption Guide 2026](https://guptadeepak.com/the-complete-guide-to-model-context-protocol-mcp-enterprise-adoption-market-trends-and-implementation-strategies/), and [Model Context Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol) (Wikipedia, which says OpenAI added MCP support to ChatGPT apps in September 2025). These are secondary sources, so the adoption timing is approximate.
[^aaif]: [MCP joins the Agentic AI Foundation](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/) (MCP blog) and [Donating the Model Context Protocol](https://anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation) (Anthropic).
[^risk]: [MCP Security Risks: Prompt Injection, Tool Poisoning, and Rug Pull Attacks](https://dev.to/deeptishuklatfy/mcp-security-risks-prompt-injection-tool-poisoning-and-rug-pull-attacks-3gk9) (DEV Community) and [Top 10 MCP Server Vulnerabilities](https://socradar.io/mcp-for-cybersecurity/security-threats-risks-and-controls/top-10-mcp-server-vulnerabilities/) (SOCRadar, which sells security products). I didn't test any of these attacks myself, and the "smallest access" and "treat results as untrusted" advice is what these sources recommend.
