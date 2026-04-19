# Contributing to Pygments Extensions

Thank you for your interest in contributing.  
This project follows the same conventions and expectations used by the Pygments core project, especially for lexer development.

Please read these guidelines before submitting a pull request.

---

## Development Setup

1. Clone the repository:
   ```
   git clone https://github.com/<your-username>/pygments-extensions
   ```
2. Create and activate a virtual environment.
3. Install development dependencies:
   ```
   pip install -e .[dev]
   ```

---

## Adding a New Lexer

Each lexer lives in its own module under `pygments_extensions/lexers/`.

A typical lexer file contains:

- a `Lexer` subclass  
- token definitions using regular expressions  
- a `tokens` dictionary  
- metadata (`name`, `aliases`, `filenames`, etc.)

Follow the same structure used in Pygments’ built‑in lexers.

### File Naming

Use lowercase, hyphen‑free filenames:

```
pli.py
oorexx.py
ispf_panel.py
```

### Class Naming

Use `CamelCase` ending in `Lexer`:

```
class PLILexer(RegexLexer):
class ooRexxLexer(RegexLexer):
class ISPFPanelLexer(RegexLexer):
```

---

## Token Rules

Token rules should follow Pygments conventions:

- Use `RegexLexer` unless there is a strong reason not to.
- Keep patterns readable and maintainable.
- Group related rules into states.
- Prefer clarity over cleverness.

Example structure:

```python
tokens = {
    'root': [
        (r'\s+', Text),
        (r'/\*', Comment.Multiline, 'comment'),
        (r'"', String, 'string'),
        ...
    ],
    'comment': [
        (r'\*/', Comment.Multiline, '#pop'),
        (r'[^*]+', Comment.Multiline),
        (r'\*', Comment.Multiline),
    ],
    'string': [
        (r'"', String, '#pop'),
        (r'[^"]+', String),
    ],
}
```

---

## Tests

Every lexer must include tests.

Place tests in:

```
tests/test_<lexername>.py
```

Tests should:

- verify tokenization of representative samples  
- include edge cases  
- follow Pygments’ testing style (simple token stream comparisons)

Example:

```python
def test_basic_tokens(lexer):
    fragment = 'IF A = B THEN;'
    tokens = list(lexer.get_tokens(fragment))
    assert tokens[0][1] == 'IF'
```

---

## Sample Files

Include sample input files under:

```
samples/<lexername>/
```

These help with:

- testing  
- documentation  
- visual inspection  

---

## Style and Formatting

- Follow PEP 8.
- Keep regexes readable.
- Add comments for complex rules.
- Match Pygments naming conventions for token types.

---

## Submitting a Pull Request

1. Ensure tests pass:
   ```
   pytest
   ```
2. Ensure your lexer has:
   - a module  
   - a lexer class  
   - tests  
   - sample files  
   - metadata  
3. Open a pull request with a clear description of the language or format.

---

## Reporting Issues

If you find a bug or want to request a new lexer, open an issue with:

- sample input  
- expected highlighting  
- references or documentation  

---

Thank you for helping improve Pygments Extensions!
