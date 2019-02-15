---
layout: default
title: Intro
nav_order: 1
permalink: /
---

# QtLing JSON

This guide documents steps of the Crab algorithm in [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) and proposes JSON structures for the input and output of each step. See [the original RFC](https://edahlgren.github.io/QtLing/design/RFC-modular-reusable-steps/) for more details.

The purpose of this guide is to demonstrate a fine-grained approach where a user has the most visibility into the linguistic data transformed and produced by the Crab algorithm. It is of course possible to combine many of the steps in this guide but these decisions should be made carefully: it is generally considered a best practice to test small units (in this case "steps") of code.

This guide is limited to the Crab algorithm (see [Phase 1](./Phase1.html) and [Phase 2](./Phase2.html)). A separate guide will cover current and future [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) graphical user interfaces.

---

#### Table of contents

---

+ [Preprocessing](./Preprocessing.html): A data preprocessing step before [Phase 1]().
+ [Phase 1](./Phase1): Steps in the first phase of the Crab algorithm.
+ [Phase 2](./Phase2): Steps in the second phase of the Crab algorithm.
+ [Appendix](./Appendix): A directory of all of the JSON structures defined in this guide.
