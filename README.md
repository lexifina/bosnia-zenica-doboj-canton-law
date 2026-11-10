# Zenica-Doboj Canton: law history in git

Part of [lexifina/global-law](https://github.com/lexifina/global-law), one git history for every country's law: this is the law of Zenica-Doboj Canton, Federation of Bosnia and Herzegovina, Bosnia and Herzegovina, which global-law reads at `bosnia-and-herzegovina/federation/zenica-doboj-canton/acts/`.

The law of Zenica-Doboj Canton (Zeničko-dobojski kanton), one of the ten cantons of the Federation of Bosnia and Herzegovina, as a git history: one file per article, one commit per law, dated the day it took effect, with the law as the commit's author. `git log` lists every change to an article; checking out a date gives the text in force that day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law), which places it at `ba-04/`. The Federation's own law is in [lexifina/bosnia-federation-law](https://github.com/lexifina/bosnia-federation-law), the state's in [lexifina/bosnia-and-herzegovina-law](https://github.com/lexifina/bosnia-and-herzegovina-law).

The text is in Bosnian (Latin script), from the Bosnian edition of the gazette; the Canton also publishes a Croatian edition of every issue.

## What this repository holds

The canton publishes the Službene novine Zeničko-dobojskog kantona on its site for 1996 to 2026; every issue listed there is read. Of the 178 Assembly laws the reader finds in them, 61 are here (from 2009), as:

- the law as enacted, dated the day it took effect; where later laws in the gazette amend it and no official consolidated text has been published since, it is marked `amended, not consolidated` and the amending laws are named (0 laws added on 2026-11-09);
- amending laws, each as an act of its own (0 added on 2026-11-09);
- official consolidated texts (prečišćeni tekst), dated the day of their issue (0 added on 2026-11-09).

The first build (October 2026) holds its laws in folders named after them; laws added later are in `zakon/<year>/sn<issue>-<act number>/`, indexed in [registry/ACTS.md](registry/ACTS.md) and [registry/data/acts.json](registry/data/acts.json).

Held back, with the reason, in [data/held.json](data/held.json) (117 laws): budget laws and laws amending them (temporary), texts that do not split into articles, laws whose in-force clause cannot be read, and texts a second, independent PDF reader does not confirm. Gazette years whose issues the reader cannot yet read (1996, 1997, 1998, 1999, 2000, 2001, 2002, 2003, 2004, 2005, 2006) are listed in data/held.json with the reason; their laws are not in the record.

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
- Whether a law was later amended or repealed is judged from every later law in the scanned issues (a law is marked `amended, not consolidated` when a later amending law cites its gazette number next to a word of its subject, or any later law cites it next to words of repeal). Decisions of the Constitutional Court are not checked.
- Health checks: no merge commits, commit dates never go backwards, nothing dated in the future, and every commit's trailers parse.

## What "author" means

The author of a commit is the law that made it, named by its gazette number, with an e-mail address that cannot exist (`<key>@zdk.ba.invalid`). The committer is always Lexifina.




## Freshness

<!-- freshness-summary -->
Checked against the official sources: 2026-11-10; 100% of acts verified in the last 7 days, 100% in the last 30 ([data/freshness.json](data/freshness.json)).
<!-- /freshness-summary -->

`python tools/freshness.py <act>` gives an act's status, its last check and the official link. A refresh runner re-reads the canton's list of gazette issues every day (at most two requests a second), reads every new issue, appends new laws and writes these files; [data/status.json](data/status.json) says whether updates are running and whether the source is answering. Acts a later law amends with no official consolidated text are marked `amended, not consolidated` and name the amending laws ([registry/data/acts.json](registry/data/acts.json)); laws and gazette years held back are listed with the reason in [data/held.json](data/held.json), and laws published but not yet in force in [data/pending.json](data/pending.json). Statuses and fields: [data/freshness.json](data/freshness.json).

## Limits

This is not an official publication. The binding text is the one published in the Službene novine Zeničko-dobojskog kantona. Only the laws listed in `data/versions.json` and `registry/data/acts.json` are included; amendments published after the last issue read are not in the record.
