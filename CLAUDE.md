# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Skills

Twee soorten skills leven onder `skills/`:

- **Gesynchroniseerd vanuit de kennisbank** — `don-apis`, `don-leidraad`, `don-security`, `don-infra`, `don-data`, `don-front-end`, `don-programmeertalen`, `don-open-source` (en andere). Deze spiegelen documentatie uit [developer-overheid-nl/don-site](https://github.com/developer-overheid-nl/don-site) en worden gegenereerd door `scripts/sync.py`. **Bewerk ze niet handmatig** — wijzigingen worden bij de volgende sync overschreven. Wijzig de bronmaterie in `don-site` zelf.
- **Handmatig beheerd** — `don-tools` (en eventuele toekomstige skills die niet in `sync.py`'s `TOPICS`/`PROMPTS`-dicts staan). Deze bevatten operationele/agent-driven inhoud (CLI-aanroepen, tool-workflows) die niet in de kennisbank thuishoort. Bewerk ze direct.

Bij het toevoegen van een nieuwe handmatige skill: zorg dat de directory-naam **niet** in `sync.py`'s `TOPICS` of `PROMPTS` staat, anders wordt hij overschreven.

## Cross-plugin referenties

Voor de **normatieve** NL GOV API Design Rules (ADR) — naming, problem+json, transport security, etc. — zie de `ls-api` skill in [developer-overheid-nl/skills-standaarden](https://github.com/developer-overheid-nl/skills-standaarden). `don-tools` linkt erheen voor de standaardregels; deze plugin bevat zelf de developer.overheid.nl-tooling (oas-generator, don-checker, schema-register, codegen) en de gesynchroniseerde kennisbank-content.

Binnen `don-tools` linken we naar de lokale gesynchroniseerde kennisbank-paden (`../don-apis/references/...`) i.p.v. naar de online developer.overheid.nl-URLs, zodat de agent ze met `Read` kan openen en de inhoud meebeweegt met de sync.

## Build & Development Commands

Sync de kennisbank-skills vanuit `don-site`:

```bash
python scripts/sync.py            # alle topics
python scripts/sync.py --topic apis  # alleen één
```
