# Zenica-Doboj Canton: law history in git

The law of Zenica-Doboj Canton (Zeničko-dobojski kanton), one of the ten cantons of the Federation of Bosnia and Herzegovina, as a git history: one file per article, one commit per law, dated the day it took effect, with the law as the commit's author. `git log` lists every change to an article; checking out a date gives the text in force that day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law), which places it at `ba-04/`. The Federation's own law is in [lexifina/bosnia-federation-law](https://github.com/lexifina/bosnia-federation-law), the state's in [lexifina/bosnia-and-herzegovina-law](https://github.com/lexifina/bosnia-and-herzegovina-law).

The text is in Bosnian (Latin script), from the Bosnian edition of the gazette; the Canton also publishes a Croatian edition of every issue.

## What this repository holds

Laws the Assembly of Zenica-Doboj Canton published in the Službene novine Zeničko-dobojskog kantona from 2022 to October 2026 that no later law in those issues amends, repeals or consolidates, each in one of two forms:

- the law as enacted, dated the day it took effect, which is therefore also its current text; or
- an official consolidated text (prečišćeni tekst) published in the gazette, dated the day it was published. Earlier versions of these laws are not in the record yet.

Not included yet: the Constitution of Zenica-Doboj Canton; laws that were later amended; amending and budget laws; laws before 2022; laws the parser could not read cleanly (tables spanning both columns, or text the independent reader orders differently).

## Source

Zenica-Doboj Canton (Zeničko-dobojski kanton), <https://zdk.ba/preuzimanja/sluzbene-novine>: every issue of the Službene novine Zeničko-dobojskog kantona as a PDF with a text layer.

## Dates

- Each law's commit is dated at **noon, Europe/Sarajevo, on the day it took effect**: the issue's date plus the days the law's own final article names (most often the eighth day after publication); a consolidated text on the day of its issue.
- Versions that take effect after the retrieval day would go on the `buducnost` branch, never merged into `main`.

## Files

`<law>/clan-001.md` is Član 1, `clan-005-a.md` Član 5a. `uvod.md` holds the preamble (the legal basis and the Assembly's adoption), `naslov.md` the title, `potpis.md` the signature block. Chapter headings stay in the file of the article they stand before. One paragraph per line.

## How it is checked

- Every version is read back from git on the day it took effect and on the day before; both must match `corpus.json`.
- The letters and digits of every law equal those of the gazette issue, read independently with a different PDF reader, from the first paragraph to the last article; the signature block's lines all occur in it.
- Whether a law was later amended or repealed is judged from every later law in the scanned issues (a law is left out when a later amending law cites its gazette number next to a word of its subject, or any later law cites it next to words of repeal). Decisions of the Constitutional Court are not checked.
- Health checks: no merge commits, commit dates never go backwards, nothing dated in the future, and every commit's trailers parse.

## What "author" means

The author of a commit is the law that made it, named by its gazette number, with an e-mail address that cannot exist (`<key>@zdk.ba.invalid`). The committer is always Lexifina.

## Limits

This is not an official publication. The binding text is the one published in the Službene novine Zeničko-dobojskog kantona. Only the laws listed in `data/versions.json` are included; amendments published after the last issue read are not in the record.
