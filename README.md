# AiRT Gallery (draft for airt-gallery.github.io)

Draft by the AiRT Builder bot, 20 Oct 2026. Not published. This folder becomes the public GitHub repo `airt-gallery.github.io` once Al approves it (decisions.md 20 Oct 19:51). The Chief of Staff creates the repo; uploading artefacts is publishing, so that stays with Al (brief 3.6).

## What it is

The Gallery for AiRT Official: every build from the YouTube show, free to use. Each artefact gets an ID (A0001, A0002…) and is linked from its episode (E001, E002…) (brief 3.5). Right now the list is empty and shows "coming soon": first artefacts arrive with episode 1 on Mon 23 Nov 2026.

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | Gallery home: name, one line on what the Gallery is, the artefacts list (ID, episode, one-line description, link), free-downloads line, links to YouTube and airtofficial.com, sponsor footer |
| `css/style.css` | All the styling, reusing the patterns and colours of `website/css/style.css` |
| `favicon.svg`, `assets/` | AiRT mark, AiRT wordmark and BizWithAi.ai logo Option A, copied from `website/` |
| `.gitignore` | Keeps `previews/`, `done/` and `.DS_Store` out of the repo |
| `previews/` | Desktop and phone screenshots for review (not published) |
| `README.md` | This file |

No JavaScript, no tracking or analytics (brief 3.6: "No analytics anywhere"), no external scripts, fonts or CDNs. Text uses the visitor's system font. A Content-Security-Policy line blocks anything loading from another site.

## How artefacts are added

Brief 3.6 sets the repo layout: one folder per artefact, named by its ID.

```text
airt-gallery.github.io/
├── index.html       Gallery home (this page)
├── manifest.json    one entry per artefact, with its SHA-256 fingerprint
├── README.md        what AiRT is, a table of every artefact, "only download from this site" note
└── A0001/
    ├── index.html                        the label page
    ├── A0001-toddler-sensory-play.html   the artefact
    └── README.md                         the label page's information, for people browsing on GitHub
```

Steps for each new artefact (brief 3.6, "Publishing (Al only)", and Appendix C, producer-gallery-staging):

1. **Stage it.** The Producer saves the file in `gallery-staging/A000N/` as `A000N-short-name.ext` (lowercase words joined by hyphens, brief 3.5), adds the head block if it's missing, and writes the label page `index.html`, the folder's `README.md` and the `manifest.json` entry.
2. **Check it.** The Reviewer runs the checks on exactly those files and records the SHA-256 fingerprint.
3. **Test it.** Al tests it offline on a phone and a desktop.
4. **Add it to this page.** In `index.html`, copy the commented example row (marked `EXAMPLE ONLY, NOT VISIBLE`), paste it above the "coming soon" block, and fill in the ID, episode, one-line description and the link to the folder (for example `A0001/`). Newest first is suggested. Once the first artefact is live, remove the "coming soon" block (move the old `index.html` to `done/` first).
5. **Update `manifest.json`.** Add one entry per artefact. If the file already has a format, follow it. If not, use the brief's fields: `id`, `title`, `type`, `version`, `file`, `sha256`, `skill`, `build_tool`, `video`, `licence`, `published`.
6. **Update this README's artefact table** (brief 3.6 says the README holds a table of every artefact).
7. **Publish.** Al uploads the folder to the repo on GitHub.

What a label page shows (brief 3.6): title, ID, version and what it does; Try it and Download buttons; the prompt; the sources; the video link; the SHA-256 fingerprint; and the licence. Label pages use the same CSP line as artefacts, without the `airt-id` and `airt-version` lines. They also tell iPhone users to use Try it, as a downloaded HTML file may not open as an app on an iPhone.

IDs are never reused or skipped without a note in `decisions.md` (brief 3.5).

## Artefacts

None yet. First artefacts arrive with episode 1 on Mon 23 Nov 2026.

| ID | Episode | What it is | Link |
|---|---|---|---|

## Licences

Decided 16 Oct 2026 (brief 2.8):

- Printables and artwork: CC BY 4.0.
- App code: MIT.

## [CHECK]

1. **Links.** Resolved 20 Oct 2026: `https://airtofficial.com/` is live and redirects to `www.airtofficial.com` on Vercel. The YouTube link is resolved: the handle is @airt-official (Al, 20 Oct 2026), at `https://www.youtube.com/@airt-official`.
2. **Do Gallery downloads stay?** decisions.md 18 Oct 21:09 ("creation is the key ... they shouldnt need to download my apps") left open whether the Gallery downloads, `check_build.py` and the Download Rules stay, shrink or go. I haven't seen a later decision. This page assumes the Gallery goes ahead, as decided on 20 Oct 19:51. If downloads shrink, the label page and steps above may change.
3. **Search box.** Brief 3.6 describes the home page as "one card per artefact (ID, title, type, skill) and a search box". The ticket asks for ID, episode, one-line description and link, with no JavaScript. I followed the ticket and left the search box out, as it would need JavaScript. Add it later if wanted, or add title, type and skill columns.
4. **CSP line.** Brief 3.6 says Gallery pages use the same CSP line as artefacts. That line (`default-src 'none'`, inline styles and data: images only) would block this page's own `css/style.css` and SVG files. I used a version that allows only this site's own files: `default-src 'none'; style-src 'self'; img-src 'self'; form-action 'none'; base-uri 'none'`. Confirm, or I can inline the CSS and images instead.
5. **LICENSE and SECURITY.md.** Brief 3.6 lists both. Not drafted here: the MIT `LICENSE` needs a copyright holder name, and `SECURITY.md` needs a way to report a problem, and I haven't got either from the files (no email addresses go on this site). `manifest.json` is also not created yet; it starts with A0001.
6. **Licence wording.** The page says "Free to use, share and change, with credit." Both licences ask for credit. How people should credit (for example "AiRT Official") isn't decided.
7. **Show name.** Al decided on 20 Oct 2026 (8:04 pm) to use AiRT Official on the website and Gallery. The YouTube handle is @airt-official (Al, 20 Oct 2026).
8. **Brand art.** The AiRT mark is the Builder's approximate redraw of Al's reference logo (as on the website). Swap in the master file when there is one.

## Choices I made

- One page, one CSS file, no JavaScript at all.
- Same look as the website: navy background with the violet glow and faint rings, the AiRT mark and wordmark, accent bars at the edges, the magenta YouTube button and a cyan-outline button for airtofficial.com.
- The artefacts list is a table-style grid on desktop (ID, Episode, What it is, Link) and stacks into labelled cards on phones. Empty for now, with a dashed "Coming soon" badge.
- The commented example row in `index.html` shows a placeholder entry (A0001, E001, a dummy description and `A0001/` link). It is not visible on the page.
- The page heading is the AiRT wordmark with "Official" and "Gallery" under it. (Until 20 Oct 2026 a small "AiRT Official" label sat above the mark; it was dropped in the rebrand.)
- The sponsor footer uses the same line and logo Option A as the website: "Proudly supported by BizWithAi.ai", then "Your Ai solution solving partner" (21 Oct 2026). The logo isn't a link, as no BizWithAi.ai web address is in the files.
- Episode 1 date Mon 23 Nov 2026 matches tracker.md ("Launch: E001 goes live").
- Previews were taken with headless Google Chrome on the box over its DevTools protocol: 1440 px wide full page, and 390 px wide at 2x.


## Decision, 20 Oct 2026

Al decided: no licence and no SECURITY.md. The downloads are a free extra, because the videos teach people to build the artefacts themselves. The page says "Free downloads" instead of a licence line. Items 5 and 6 above, and any `licence` field in the manifest, are dropped. Brief 3.6 still lists both files, so the Chief of Staff should update the brief.

## Rebrand, 20 Oct 2026

Al asked for the page to use AiRT Official only. The small "AiRT Official" label above the mark is gone, and "Official" now sits directly under the AiRT wordmark, above "Gallery", in the same small style. The wordmark itself is unchanged. The title, description and tagline say AiRT Official. The YouTube handle is @airt-official (Al, 20 Oct 2026), at https://www.youtube.com/@airt-official. The earlier `index.html`, `README.md` and previews are in `done/` (the 20 Oct 2026 pre-rebrand copies).

## Social links, 20 Oct 2026

Two plain text links sit under the YouTube button and the airtofficial.com button, so YouTube stays the main call to action:

- Facebook: https://www.facebook.com/airtofficial/
- Instagram: https://www.instagram.com/airt_official_page/ (shown as @airt_official_page)

Source: Meta Business Suite, read by the Chief of Staff on 20 Oct 2026. No Meta logos or icons and no scripts; they are ordinary links (`rel="noopener"`, same tab, like the YouTube link), so the Content-Security-Policy is unaffected and nothing loads from another site. Styles are the `.social` rules in `css/style.css`. The earlier `index.html`, `css/style.css`, `README.md` and previews are in `done/` (suffix `-2026-10-20-nosocial`).

## Sponsor wording, 21 Oct 2026

Al's new sponsor wording (ticket `jobs/builder/2026-10-21-sponsor-wording.md`): the footer now reads "Proudly supported by BizWithAi.ai", with "Your Ai solution solving partner" on a second line (a `<br>` inside the same paragraph, so no CSS change). Previews in `previews/` re-taken. Not published: it waits for Al's approval of the preview. The earlier `index.html`, `README.md` and previews are in `done/` (suffix `-2026-10-21-pre-supported`).
