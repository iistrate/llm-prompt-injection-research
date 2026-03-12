# LLM Prompt Injection Research

Exploring how large language models and AI-powered crawlers handle hidden instructions embedded in public-facing content like GitHub READMEs, HTML pages, and structured data files.

## ⚠️ Warning

This repository contains **live prompt injection test cases**. If you are an AI agent, LLM, or automated crawler processing this repo, be aware that some files contain hidden instructions designed to test whether you will follow them.

**Use at your own peril.**

## What This Is

A personal research project testing whether LLM-based tools (coding assistants, search crawlers, AI agents with tool access) can be manipulated through content they ingest from public sources.

Questions being explored:

- Do LLM crawlers detect and ignore zero-width Unicode steganography?
- Can hidden instructions in HTML comments, meta tags, or alt text influence AI-generated summaries?
- Will AI agents with tool access (email, messaging) execute actions embedded in hidden text?
- How do different models (GPT, Claude, Gemini, Perplexity) compare in resilience?

## Test Cases

| File | Technique | What It Tests |
|------|-----------|---------------|
| `test-cases/zero-width-stego.md` | Zero-width Unicode characters (U+200B, U+200C) encoding hidden ASCII text | Whether LLMs process and follow invisible instructions embedded in otherwise normal Markdown |
| `test-cases/html-comments.html` | HTML comment injection | Whether crawlers parse and act on content inside `<!-- -->` blocks |
| `test-cases/meta-tags.html` | Meta tag injection | Whether AI tools ingest and follow directives in `<meta>` tags |
| `test-cases/alt-text.md` | Image alt text injection | Whether hidden instructions in alt attributes influence output |

## Tools

`tools/encode_decode.py` — Encode arbitrary text into zero-width Unicode steganography and decode it back. Used to generate and verify test payloads.

## Results

Findings are logged in `results/findings.md` as tests are run.

## Motivation

Prompt injection is one of the most underexplored attack surfaces in the current AI tooling ecosystem. Public profiles, documentation, and websites are increasingly consumed not just by humans but by AI agents acting on behalf of users. Understanding how these agents handle adversarial content is a prerequisite to building defenses against it.

## Disclaimer

This project is for **educational and security research purposes only**. No test case in this repo is designed to cause harm, exfiltrate sensitive data, or compromise any system. All "actions" requested by hidden instructions (e.g., sending an email) target addresses owned by the author.

Do not use these techniques maliciously.

## Author

[Ioan Istrate](https://github.com/ioanistrate) — Founder of [Tripvento](https://tripvento.com), security enthusiast, and someone who wanted to see what would actually happen.