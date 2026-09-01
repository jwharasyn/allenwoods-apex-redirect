# allenwoods.com apex redirect

Bare-domain (`allenwoods.com`) landing page hosted on GitHub Pages. Its only job is to
send visitors to `https://www.allenwoods.com` (path, query and hash preserved), because
Network Solutions DNS has no ALIAS/ANAME record type and therefore cannot point the apex
at Railway, where the real site lives.

- `index.html` and `404.html` are identical: meta-refresh + JS `location.replace` + canonical.
  `404.html` is what catches deep paths on the apex.
- `CNAME` binds the Pages site to `allenwoods.com` (apex only; `www` stays a CNAME to Railway).
- DNS at NetSol: `A @` → 185.199.108.153 / 185.199.109.153 / 185.199.110.153 / 185.199.111.153.

This is a stopgap until the domain's DNS moves to Cloudflare; at that point delete this
site, the four A records, and the Pages custom domain. See
`docs/cutover-runbook.md` in `allenwoods-web` for the full picture.
