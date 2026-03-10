---
title: "On Writing Documentation That People Actually Read"
date: 2024-02-03
description: "Documentation fails when it's written for the author, not the reader. A few principles I've picked up."
tags: [writing, engineering, documentation]
---

Most documentation is written to be written, not to be read.

You can feel it in the prose — breathless lists of features, passive voice, the eerie confidence of someone explaining a thing they built to someone who wasn't there when they built it.

I've written that documentation. I've also been the person who needed it at 11pm with a deadline.

## The problem isn't laziness

Engineers who write bad docs aren't lazy. They're often the opposite — they care deeply and write exhaustively. The problem is a failure of perspective.

When you know a system intimately, you can't unknow it. Every sentence you write is filtered through that knowledge. The gaps are invisible to you because you filled them years ago.

This is called the **curse of knowledge**, and it's the central challenge of technical writing.

## What actually helps

**Write the error message first.** Before you document how something works, document what happens when it breaks. That's when people actually read docs.

**One concept per section.** If you need a sentence that starts with "and also" or "additionally", that's a new section.

**Test your docs.** Find someone unfamiliar with the system. Watch them try to follow your instructions. Don't help them. Take notes.

**Date everything.** Undated documentation is a lie waiting to happen.

## The real test

Imagine you're paged at 2am. The system is down. You have your own documentation in front of you.

Does it help?

If you're not sure, it probably doesn't.
