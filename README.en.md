# architecture-designer

[简体中文](README.md) | **English**

**Design the skeleton before writing code: layers, module boundaries, tech choices, extension points. Produces `06-architecture-design.md` behind a script gate.**

![Python](https://img.shields.io/badge/python-3.9%2B-3776AB)
![Dependencies](https://img.shields.io/badge/pip%20install-0%20dependencies-2E7D32)
![License](https://img.shields.io/badge/license-MIT-yellow)
![spec](https://img.shields.io/badge/agentskills.io-spec%20valid-2E7D32)

## Install

```bash
npx skills add zhanguoliang715/architecture-designer
```

Or as a Claude Code plugin:

```bash
claude plugin marketplace add zhanguoliang715/architecture-designer
claude plugin install architecture-designer@architecture-designer
```

## Why a dedicated baton for architecture

Bad architecture does not show up as ugly code. It shows up as **the second feature being impossible to add**:

- no layering, so business logic and SQL live in one file and swapping the database means touching everything;
- no module boundaries, so two modules read each other's tables and one change breaks two features;
- no extension points, so adding "due-date reminders" requires editing five existing files;
- no recorded rationale, so six months later nobody dares change the choice and nobody remembers why it was made.

This skill turns that into a fixed six-section document that a script can partially verify, and that the implementation baton can follow mechanically.

## Output structure (six fixed sections)

```
1. Overview        one sentence + textual layer diagram
2. Layers          layer / responsibility / depends on / key components
3. Modules         module / responsibility / public interface / dependencies
4. Tech choices    concern / choice / rationale
5. Extensibility   how new features plug in + how the data model evolves
6. Constraints     directory layout, naming, dependency direction
```

## Entry gate

Before designing anything: the requirement review must be **YES**, the PRD must contain an FR list, and the database design must be finalized. Missing any of the three means stop — do not design on guesses.

## What it is not

- **Not general architecture advice.** It assumes a mid-size web project. Embedded firmware, algorithm libraries, and data scripts barely use the layer and module sections.
- **Not a code generator.** It produces the skeleton, not the implementation.
- **Not a microservice splitter.** The default shape is a layered monolith.

## Docs

- [Beginner handbook](docs/新手手册.md) — how to do it step by step.
- [Technical doc](docs/技术文档.md) — contracts, checker behaviour, known limits, failure modes.
- [Example artifact](examples/06-architecture-design.example.md) — passes the checker (exit 0), ready to adapt.

## License

MIT.
