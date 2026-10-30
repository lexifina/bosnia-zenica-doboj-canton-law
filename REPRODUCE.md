# How this repository was made (Zenica-Doboj Canton)

This file is written by the build on 2026-10-30, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| Zeničko-dobojski kanton: Službene novine Zeničko-dobojskog kantona (each issue as a PDF, Bosnian edition) | <https://zdk.ba/preuzimanja/sluzbene-novine?view=single&layout=table&id=103&show_title=1&show_description=1> | 2026-10-30 | Official text, not protected: Zakon o autorskom i srodnim pravima BiH (Sl. glasnik BiH 63/10), čl. 8(1)(b) |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `o-mirnom-okupljanju` | Zakon o mirnom okupljanju | 1 | 2023-12-20 to 2023-12-20 |
| `o-mirovnom-i-arbitraznom-vijecu` | Zakon o mirovnom i arbitražnom vijeću | 1 | 2024-04-19 to 2024-04-19 |
| `o-socijalnoj-zastiti-zastiti-civilnih-zrtava-rata-i-zastiti` | Zakon o socijalnoj zaštiti, zaštiti civilnih žrtava rata i zaštiti porodice sa djecom -prečišćeni tekst- | 1 | 2025-03-24 to 2025-03-24 |
| `o-obiljezavanju-znacajnih-datuma` | Zakon o obilježavanju značajnih datuma | 1 | 2025-10-21 to 2025-10-21 |
| `o-porezu-na-promet-nekretnina` | Zakon o porezu na promet nekretnina | 1 | 2026-01-08 to 2026-01-08 |
| `o-prijavljivanju-i-postupku-provjere-podataka-o-imovini-nosi` | Zakon o prijavljivanju i postupku provjere podataka o imovini nosilaca javnih funkcija | 1 | 2026-06-06 to 2026-06-06 |

The build made 6 commits:

| Commits | Kind |
| ---: | --- |
| 6 | first version of an act |
| 0 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `buducnost`: laws not yet in force on 2026-10-30.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 6 laws in the record.
- 11 tags.

## Dates

Each commit is dated at noon (Europe/Sarajevo) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: A law takes effect on the day its own final article names, counted from its publication in the Službene novine Zeničko-dobojskog kantona. https://zdk.ba/preuzimanja/sluzbene-novine?view=single&layout=table&id=103&show_title=1&show_description=1

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `14040d75d752e304d09e87351c4a950cfdafdf14f144c218bb14535e76a19932` (240452 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `900da0d33bfd1ef455267fb4dcef7961fd5acc9c`, `check.py` `5d719354ea4c62d240c93d2cae446307d81d9e81`, `on.py` `aff48cf1b68d50c7ba8f399ca32261871c301824`.
- Python 3.14.4; git version 2.53.0.

## Checks

6 versions of 6 acts read back from git on the day each took effect and on the day before: 0 mismatches. Trailers: 0 commits whose trailers git cannot parse. Health: 0 merge commits on main, 0 commit dates that go backwards, 0 commits dated after the build.

No second build of this corpus has been compared yet.

## Decisions made by hand

- Laws part 1: laws the Assembly of Zenica-Doboj Canton published in the Službene novine Zeničko-dobojskog kantona from 2022-01-01 to 2026-10-26 (the Bosnian edition of every issue on zdk.ba in that span; laws are checked against every later issue) that no later law in those issues amends, repeals or consolidates: a law is left out when any later amending law or consolidated text cites its gazette number next to a word of its subject, or any later law cites it next to words of repeal. Amending and budget laws are left out. Each is its text as enacted, dated the issue date plus the days its final article names, credited to the law; or, where the Legislative Committee of the Assembly has published an official consolidated text (prečišćeni tekst) that nothing later touches, that text, dated the day it was published (it applies from its publication, as its last article says). Amendments published after 2026-10-26, and decisions of the Constitutional Court, are not in the record.
- Each law is taken from the Bosnian edition of the gazette (the Canton also publishes a Croatian edition of every issue).
- Units: uvod.md is the preamble (legal basis and adoption), naslov.md the title, clan-NNN.md each article with its heading (chapter headings stay with the article after them), potpis.md the signature block.

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- none: the text is read from the gazette PDFs' text layer by a deterministic parser; no model output is legal text.
