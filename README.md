# Pwn Kent website

A one-page static site for **pwnkent.co.uk**, ready for GitHub Pages.

- No cookies; the only script is GoatCounter's privacy-friendly page counter (pwnkent.goatcounter.com)
- Fonts are self-hosted (SIL Open Font License, see `fonts/`)
- A strict Content Security Policy is set in the page's `<head>`. It only allows GoatCounter's script (gc.zgo.at) and its counting endpoint (pwnkent.goatcounter.com). If you add any other service later, add its domain to that policy too, or the browser will block it.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole site |
| `favicon.svg` | Browser tab icon |
| `og-image.png` | Preview image shown when the link is shared on LinkedIn, Slack and so on |
| `fonts/` | JetBrains Mono and Space Grotesk, plus their licences |
| `CNAME` | Tells GitHub Pages to serve the site at pwnkent.co.uk |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is |

## 1. Buttons and contact links

For now, every button (Register interest, Offer a talk, Count me in) and every contact link points to Sam's LinkedIn profile. To change it later, search `index.html` for `linkedin.com/in/sam-macdonald-66967642` and replace every occurrence.

## 2. Later: a proper sign-up form (optional)

When you want sign-ups in one list instead of LinkedIn messages, create a free Tally form, point the buttons at its share link, and update the "Who handles it" part of the privacy notice. Suggested form at tally.so, called "Pwn Kent: register interest":

1. Name (short answer, required)
2. Email (email, required)
3. Which night suits you best? (multiple choice: Monday, Tuesday, Wednesday, Thursday, No preference)
4. Would you be up for giving a talk? (checkbox: Lightning talk, Main talk)
5. Anything else? (long answer, optional)
6. Consent (checkbox, required): "I'm happy for Pwn Kent to email me about meetups. I can unsubscribe at any time."

Publish it, then use its share link for the buttons.

## 3. Put it on GitHub

1. Create a new public repository, for example `pwnkent`. Optionally create a free `pwnkent` GitHub organisation first and put the repo there, so co-organisers can help later.
2. Upload every file in this folder, including `.nojekyll`, `CNAME` and the `fonts` folder. On a Mac, press Cmd+Shift+. in Finder to show the hidden `.nojekyll` file.
3. Go to **Settings > Pages**. Under *Build and deployment*, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. Under **Custom domain**, enter `pwnkent.co.uk` and save.

## 4. Point the domain at GitHub (GoDaddy DNS)

In GoDaddy, open the DNS settings for pwnkent.co.uk:

1. Delete any existing **A** record for `@` (GoDaddy often adds a "Parked" record).
2. Add four **A** records, each with name `@`:
   - `185.199.108.153`
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`
3. Add a **CNAME** record with name `www`, pointing to `YOUR-GITHUB-NAME.github.io` (or the organisation's name).

DNS can take from a few minutes to a few hours to update. Once GitHub shows the domain as verified, tick **Enforce HTTPS** in Settings > Pages.

Check these A record addresses against GitHub's own guide before saving: search "GitHub Pages managing a custom domain".

## Updating the site

- **Launch progress bar:** in `index.html`, find `--progress:70;` near the top of the styles and change the number (0 to 100). Also update `aria-label="Launch progress: 70 percent"` to match.
- **Meetup details:** edit the `meetup.conf` block (date, time, venue).
- **Launch date:** search for `Early 2027` (2 places) and replace it with the real date.

## Before the London conference

The hoodie's QR code points to https://pwnkent.co.uk, so make sure the site is live and the Tally link works. Then scan the code from a printed test with a couple of different phones.
