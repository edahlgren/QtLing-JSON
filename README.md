---
layout: default
title: Intro
nav_order: 1
permalink: /
---

# QtLing JSON

This guide documents steps of the Crab algorithm in [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) and proposes JSON structures for input and output to each step. See [the original RFC](https://edahlgren.github.io/QtLing/design/RFC-modular-reusable-steps/) for background.

The purpose of this guide is to demonstrate a fine-grained approach where a user has the most visibility and control over linguistic data produced by the Crab algorithm. It is worth noting that a fine-grained approach provides opportunities for smaller steps in terms of lines of code and it is generally considered a best practice to test small units of code to decrease debugging time.

This guide only covers the Crab algorithm (see [Phase 1](./Phase1.html) and [Phase 2](./Phase2.html)). A separate guide will cover integrating the JSON output of individual steps with a user interface.
