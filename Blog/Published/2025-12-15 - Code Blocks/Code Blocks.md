---
status: Published
description: Syntax highlighting, file labels, line highlighting—all the code stuff.
posted on: 2025-12-15
favorite: false
tags: []
"[draftist] content kind": BlogPost
"[draftist] content id": 019b8897edf27bb2b2f395f21e5d6d99
"[draftist] published title": Code Blocks
"[draftist] published slug": code-blocks-bvweaua6g
"[draftist] published on": 1784825461226
---
Code is everywhere in technical writing. Here's how it looks when published with [Draftist](https://draftist.io/). ^11db50

## Basic Code Blocks ^57ec2f

Drop in a code block with a language identifier and syntax highlighting just works: ^d9a5e4

```rust
pub struct TokenStream<'a> {
    tokens: &'a [Token],
    position: usize,
}

impl<'a> TokenStream<'a> {
    pub fn peek(&self) -> Option<&Token> {
        self.tokens.get(self.position)
    }

    pub fn advance(&mut self) -> Option<Token> {
        let token = self.tokens.get(self.position).cloned();
        self.position += 1;
        token
    }
}
```
^44fe6b

## File Labels ^075a3d

You can label your code with the `file` attribute to add a filename in the header—useful when showing code from a specific file: ^3d87a1

```rust file=token_stream.rs
pub fn expect(&mut self, kind: TokenKind) -> Result<Token> {
    match self.advance() {
        Some(token) if token.kind == kind => Ok(token),
        Some(token) => Err(ParseError::unexpected_token(token, kind)),
        None => Err(ParseError::unexpected_eof()),
    }
}
```
^7acd83

## Line Highlighting ^589ba5

You can `highlight` specific lines in the code to draw attention to specific areas. Here, lines 8-11 show the core loop logic: ^74111f

```rust file=combinators.rs highlight=8-11
pub fn separated_list<T>(
    parser: &mut Parser,
    separator: TokenKind,
    element: impl Fn(&mut Parser) -> Result<T>,
) -> Result<Vec<T>> {
    let mut items = vec![element(parser)?];

    while parser.stream.peek().map(|t| t.kind) == Some(separator) {
        parser.stream.advance();
        items.push(element(parser)?);
    }

    Ok(items)
}
```
^1d0d07

## Captions ^8fe05a

The `caption` attribute adds a description below the code block: ^7e3e92

```rust file=parser.rs caption="Error recovery skips to the next statement boundary after a parse error"
impl Parser {
    fn synchronize(&mut self) {
        while let Some(token) = self.stream.peek() {
            match token.kind {
                TokenKind::Semicolon => {
                    self.stream.advance();
                    return;
                }
                TokenKind::Fn | TokenKind::Let => return,
                _ => self.stream.advance(),
            }
        }
    }
}
```
^4cbf75

## Multiple Languages ^2004ba

Syntax highlighting works across languages: ^5f730d

```js file=handler.js
async function fetchData(url) {
    const response = await fetch(url);
    if (!response.ok) {
        throw new Error(`HTTP error: ${response.status}`);
    }
    return response.json();
}
```
^1db676

```python file=processor.py
def process_items(items):
    return [
        item.upper()
        for item in items
        if item.startswith('_')
    ]
```
^56ef9b

```rescript file=User.res
type user = {
  id: int,
  name: string,
  email: option<string>,
}

let display = user =>
  switch user.email {
  | Some(email) => `${user.name} <${email}>`
  | None => user.name
  }
```
^7dfff6

```typescript file=types.ts
interface User {
    id: number;
    name: string;
    email?: string;
}

type Result<T> =
    | { success: true; data: T }
    | { success: false; error: string };
```
^82c203

## Inline Code ^d567fb

Use backticks for inline code like `TokenKind::LParen` or `Result<T>` within text. ^04690b

## Combining Everything ^de2d0d

All attributes work together. Here the highlighted lines show the `expect` calls that enforce the delimiters: ^74b08d

```rust file=delimited.rs highlight=7,9 caption="Helper for parsing delimited expressions like (foo) or [bar]"
pub fn delimited<T>(
    parser: &mut Parser,
    open: TokenKind,
    inner: impl Fn(&mut Parser) -> Result<T>,
    close: TokenKind,
) -> Result<T> {
    parser.stream.expect(open)?;
    let result = inner(parser)?;
    parser.stream.expect(close)?;
    Ok(result)
}
```
^30214c

---

That's it for code blocks. Syntax highlighting, file labels, line highlights, and captions—use them to make your code samples clear and nice looking. ^e33560
