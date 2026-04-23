---
title: A Post With No Author Front-Matter
date: 2026-02-01
tags:
  - sample
---

This post deliberately omits the `author:` field in its front matter so
that CI can verify the theme's dynamic-author chain falls back to
`.Site.Params.author`.
