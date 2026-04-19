# Pygments Extensions

A collection of community‑maintained lexers that extend the Pygments syntax‑highlighting ecosystem.  
This project provides high‑quality, fully‑tested lexers for languages and formats that are widely used but not yet supported in the Pygments core distribution.

The goal is to offer a unified, platform‑agnostic home for new and emerging lexers, making them easy to install, easy to maintain, and easy to contribute to.

---

## Included Lexers

This repository will host multiple lexers, including:

- **PL/I**
- **ooRexx**
- **ISPF formats**
  - Panels  
  - Messages  
  - Skeletons  
  - DTL
- **Future lexers** (Contemplated)
  - HLASM  
  - JCL  
  - CMS Pipelines  
  - others as needed

Each lexer is developed as a standalone module but maintained under a single project umbrella for consistency and long‑term support.

---

## Project Goals

- Provide high‑quality lexers for under‑served languages and formats  
- Maintain compatibility with upstream Pygments  
- Support Wikimedia and other platforms that rely on Pygments  
- Encourage community contributions  
- Keep the project platform‑neutral and future‑proof

---

## Installation

The project will be published on PyPI once the initial lexers are finalized.

```
pip install pygments-extensions
```

(Placeholder — package not yet published.)

---

## Contributing

Contributions are welcome.  
Each lexer lives in its own module with:

- tests  
- sample input files  
- documentation  
- style and naming conventions aligned with Pygments core

Open an issue or pull request to propose new lexers or improvements.

---

## License

MIT License (same as Pygments).
