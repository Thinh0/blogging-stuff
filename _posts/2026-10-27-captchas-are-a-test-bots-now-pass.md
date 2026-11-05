---
layout: post
title: "What is CAPTCHA? Can AI solve it?"
subtitle: "We keep making humans prove they're human, and the machines keep getting better at it"
categories: [web]
---

When i was in middle school, every few days i was stopped by CAPTCHA when accessing websites. It asked me whether I am a robot. Of course I'm not. Then i asked my self, how clicking on the right images tells me and the robot apart? Don't they capable of that as well? The CAPTCHA even got simpler now by just clicking the "I'm not a robot" then you're good to go. So I wonder how all the CAPTCHAs work that it can decide which is human and which is a bot. Also, can AI these days solve CAPTCHAs?

## Where it came from

The word "CAPTCHA" came around in the early 2000s, from Luis von Ahn and some other people at Carnegie Mellon University. It's short for "Completely Automated Public Turing test to tell Computers and Humans Apart". Long name, simple idea: find something that people do easily but computers are bad at, and use it as a gate. Back then that meant reading squiggly, warped letters.

Then came reCAPTCHA in 2007, and it had a clever trick. The words you were typing came from old scanned books that computers couldn't read, so every time someone passed the test, they also helped turn a book into text. Google bought it in 2009. After that the warped words turned into street numbers, then those "click all the traffic lights" grids.[^history]

## So how does "I'm not a robot" work?

This one surprised me. The checkbox itself is not the test. What the website really looks at is how you act before and during the click: how your mouse moves, how fast you type, and what your browser looks like. If all that looks like a normal person, you get through with one click. If it looks off, that's when you get the traffic light pictures. Later versions (reCAPTCHA v3) skip the question completely and just give you a score in the background. Cloudflare's Turnstile, which came out in 2022, does a similar thing.[^history]

So to answer my own question: clicking the right images was never really about being smart. It was about something being easy for a human and hard for a computer. The problem is that "hard for a computer" keeps changing.

## Can AI solve them now?

Pretty much, yes. Every CAPTCHA is basically a test that a computer is supposed to fail, and people who build AI are very good at making computers pass tests. Squiggly text got beaten by better text reading. Picture grids got beaten by better image recognition.

Here are the numbers I found, but they came from articles about the studies and not the studies themselves, so take them with a grain of salt:

- A 2024 study from ETH Zurich supposedly had an AI model solving reCAPTCHA v2 picture puzzles almost every time.
- A newer report says a free program running on a normal computer passed about 463 out of 500 real reCAPTCHA tests, which is around 92%.[^ai]

I didn't read the original papers, so I wouldn't repeat the exact percentages as facts. But the overall point is the same everywhere I looked: the puzzle part of CAPTCHA doesn't stop a determined bot anymore.

## The people who get stuck with the bill

If bots get through anyway, then the ones who actually get annoyed are real people. The W3C (the group that writes the rules for the web) says a CAPTCHA takes about 32 seconds on average, and longer for people with disabilities. Some can't do them at all. If you can't see the pictures, you're stuck, and the audio version is often so distorted that it's hard to understand too.[^w3c]

It's not just a few people either. One survey of over 250 people found that they get more frustrated as the puzzles get harder, and they don't really trust that these things keep them safe.[^survey] Some people have also tried to add up all the time humanity has wasted on CAPTCHAs and got numbers in the hundreds of millions of hours, but I've only seen that in summaries, so I'm not going to quote one.[^hours]

So the deal right now is that humans lose time and sometimes get locked out, and the bots mostly get in anyway. That doesn't feel like a great deal.

## What's replacing it

Websites are moving from "prove you're human" to "we'll quietly decide for you". That means watching how you behave, looking at your browser and device, and sometimes making your computer do a little bit of math work (called proof-of-work) that's cheap for one person but gets expensive for a bot sending millions of requests.[^pow]

I like that I don't see puzzles as much. But I'm not sure it's actually better. The annoying part didn't go away, it just went somewhere I can't see. And a lot of what they use to decide sounds a lot like tracking. If the system decides I'm a bot, there's no puzzle to try again. It's just a closed door.

Money is part of this too. Google cut the free tier of reCAPTCHA from 1 million checks a month down to 10,000, so a lot of smaller sites started looking at other options. Most sources say that happened in 2024, but one says 2026, so I'd check Google's own pricing page before trusting either.[^pricing]

## What about AI agents?

Here's the part I find the most interesting. More and more, the "bot" visiting a website isn't a scammer. It's an AI assistant doing something for a real person, like booking a trip or comparing prices. A CAPTCHA can't tell the difference between that and a bad bot, so it blocks both. Meanwhile, the real bad guys use paid services that solve CAPTCHAs for them.[^agents]

That kind of breaks the whole idea. "Is this a human?" was always just a stand-in for "is this someone I want on my site?", and those two questions are splitting apart. A human using an AI assistant is a human, but it's also a bot. And a bad bot can act so much like a human that it passes the test anyway. What websites really want to know is whether the visitor means well, and no puzzle can show that.

## Where I land

I think the puzzle kind of CAPTCHA is on its way out, and I won't miss it. I just hope what takes its place doesn't track everything I do, and doesn't lock out people who can't do the test. I don't have an answer for that. Proof-of-work sounds nice because it asks for effort and not for who you are, but it's an arms race too, and it doesn't help with the AI assistant problem.

For now, here's how I'd sum it up: we made a test to tell people and machines apart, the machines learned to pass it, and we kept making the people take it.

## References

[^history]: Overview of how CAPTCHA changed over time, from warped text to reCAPTCHA to behavior scoring and Turnstile: [CAPTCHA Security in 2026: How Proof-of-Work and Risk Signals Work Together](https://friendlycaptcha.com/insights/captcha-security/) (Friendly Captcha, which sells this stuff, so keep that in mind) and [Cloudflare Turnstile vs reCAPTCHA: 5 Key Differences](https://nexterwp.com/blog/cloudflare-turnstile-vs-google-recaptcha/).
[^ai]: [Why CAPTCHAs Are Losing Ground to AI](https://c3.unu.edu/blog/captchas-losing-ground-to-ai) (UNU Campus Computing Centre); [As AI solves CAPTCHAs, what's next?](https://www.itbrew.com/stories/2025/09/30/as-ai-solves-captchas-what-s-next) (IT Brew); [AI Bots Are Making Traditional CAPTCHA Less Effective](https://news.designrush.com/ai-bots-captcha-website-security-ux) (DesignRush). The ETH Zurich and 463-of-500 numbers are as these articles reported them. I didn't check the original papers.
[^w3c]: [Inaccessibility of CAPTCHA](https://www.w3.org/TR/turingtest/Overview.html), W3C.
[^survey]: Reddy and Cheng, [User Perception of CAPTCHAs: A Comparative Study between University and Internet Users](https://arxiv.org/abs/2405.18547) (arXiv, 2024).
[^hours]: [Summary of the UC Irvine reCAPTCHA v2 study](https://www.techbang.com/posts/121342-captchas-waste-billions-of-user-hours-research-unravels-the) (Techbang, secondhand).
[^pow]: [CAPTCHA Security in 2026: How Proof-of-Work and Risk Signals Work Together](https://friendlycaptcha.com/insights/captcha-security/) (Friendly Captcha).
[^pricing]: [Google reCAPTCHA price changes](https://prosopo.io/blog/google-recaptcha-price-changes) (Prosopo, a competitor); [reCAPTCHA Pricing in 2026](https://phpcaptcha.org/recaptcha-pricing/) (the source that gives a 2026 date).
[^agents]: [Bot Protection in the Age of AI Agents (2026)](https://agentpedia.codes/blog/bot-protection-ai-agents-2026).
