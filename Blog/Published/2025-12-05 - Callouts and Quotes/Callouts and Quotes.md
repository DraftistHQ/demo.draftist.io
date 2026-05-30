---
status: Published
description: Highlight important bits, warn readers, show examples.
posted on: 2025-12-05
tags: []
"[draftist] content kind": BlogPost
"[draftist] content id": 019b8898f49a7dd3900a22bedcfe3766
"[draftist] published title": Callouts and Quotes
"[draftist] published slug": callouts-and-quotes-0pfs7u1c0
"[draftist] published on": 1780168652208
---
Callouts are those colored thingies that highlight important information. Blockquotes are for, well, quoting stuff. Here's how they look like. ^f25af8

## Callout Types ^3acd78

Different types for different purposes: ^4a442a

> [!note]
> General information that supplements the main text.
^f21b39

> [!info]
> Similar to note, but emphasizes informational content.
^0b4c22

> [!tip]
> Helpful advice or best practices.
^ba33d3

> [!link]
> Highlight related resources or external references.
^827ba6

> [!warning]
> Something to watch out for.
^6f6e6a

> [!danger]
> Critical issues requiring immediate attention.
^072d7d

> [!success]
> Positive outcomes or completed tasks.
^b9bee2

> [!failure]
> Errors or unsuccessful operations.
^2bccfd

> [!question]
> FAQs or prompts for consideration.
^a46103

> [!example]
> Concrete examples or code snippets.
^4e3f0c

## Custom Titles ^527a4b

Callouts can have titles: ^11ff5f

> [!warning] Breaking Change
> This API will change in version 2.0. Check the migration guide before upgrading.
^46ea7b

> [!tip] Performance Optimization
> Batch operations reduce overhead when processing large datasets.
^eced73

## Collapsible Callouts ^8b5702

You can make a callout collapsed by default (click to expand): ^c0f296

> [!note]- Collapsed by default
> This content is hidden until you click the callout header. Useful for lengthy details that not everyone needs to see.
^921074

And you can make it expanded by default but still collapsible: ^22b3b9

> [!tip]+ Expanded by default
> This starts open but can be collapsed. Good for optional content that most readers will want to see.
^3ba596

## Rich Content ^f52237

Callouts can contain paragraphs, lists, code, images, and more: ^12d9e3

> [!example] Mixed Content
>
> Here's a paragraph explaining the concept.
>
> A list of requirements:
> - Rust 1.70+
> - Basic Rust knowledge
> - A text editor
>
> And some code:
> ```rust
> let users: Vec<User> = db.query("SELECT * FROM users").await?;
> println!("{:#?}", users);
> ```
^f238e0

## Blockquotes ^3887ea

Standard markdown blockquotes are turned into quotations: ^17dbfc

> Design is not just what it looks like and feels like. Design is how it works.
^8f6566

You can them with optional attribution: ^740bad

> Any fool can write code that a computer can understand. Good programmers write code that humans can understand.
>
> -- Martin Fowler
^51890c

---

That covers callouts and quotes. Use them to break up walls of text and highlight what matters. ^1e87a0
