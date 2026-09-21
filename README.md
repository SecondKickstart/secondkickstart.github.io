# secondkickstart.github.io

Source for **secondkickstart.com** — the public site for the Second Kickstart YouTube channel.

Single static page. No build step, no dependencies. `index.html` is the whole site;
fonts load from Google Fonts, everything else is inline.

## Hosting

Published with GitHub Pages from the `main` branch, root folder.

Repo → **Settings → Pages**
- Source: *Deploy from a branch*
- Branch: `main`, folder `/ (root)`
- Custom domain: `secondkickstart.com`
- Enforce HTTPS: on (the checkbox appears once the certificate is issued — up to 24h)

Setting the custom domain in that screen creates a `CNAME` file in this repo. Leave it alone.

## DNS (GoDaddy)

Four A records and four AAAA records on the apex, plus one CNAME for `www`:

| Type  | Name | Value |
|-------|------|-------|
| A     | @    | 185.199.108.153 |
| A     | @    | 185.199.109.153 |
| A     | @    | 185.199.110.153 |
| A     | @    | 185.199.111.153 |
| AAAA  | @    | 2606:50c0:8000::153 |
| AAAA  | @    | 2606:50c0:8001::153 |
| AAAA  | @    | 2606:50c0:8002::153 |
| AAAA  | @    | 2606:50c0:8003::153 |
| CNAME | www  | secondkickstart.github.io |

Delete GoDaddy's default parked A record on `@` first, or it fights these.

**Do not touch the MX or TXT records** — those carry Microsoft 365 mail for
`press@secondkickstart.com`, plus SPF, DKIM and DMARC. Website records and mail
records are different record types and coexist fine; the only real risk is a bulk
"reset DNS" or turning on GoDaddy's website forwarding, either of which will
break email.

## Editing

Change `index.html` and commit to `main`. Pages rebuilds in under a minute.

Content that goes stale first:
- the **In production** slate — move a video to published, with a link, once it's live
- the manufacturer lists under each video, as the lineups firm up
- **Editorial standards** — these are quoted almost verbatim in the press-outreach
  emails, so if the wording changes here, it should change there too
