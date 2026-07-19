# DEPLOY — grokmcp.org cutover checklist

Step-by-step for cutting the ChatGPT Sites deployment over to this repo.

## 1. Create the new GitHub repo and push

Suggested name: `grokmcp-org-site` (any name works).

```bash
cd grokmcp-org-site
git init
git add .
git commit -m "Initial static site for grokmcp.org"
git remote add origin git@github.com:djtelicloud/grokmcp-org-site.git
git push -u origin main
```

## 2. Repoint the ChatGPT Sites source

In ChatGPT Sites settings for the grokmcp.org app, point the site's source at the **new** repo.

Honest note — the exact control may be either or both of:

- The site's **GitHub connection / repo picker** — if it exists, use it, and the env var below can be deleted.
- The **`GITHUB_REPOSITORY`** environment variable, currently set to `djtelicloud/grok-mcp-server` — if that env var is the source selector, update it to the new repo.

## 3. Redeploy

Trigger a new build / redeploy from the Sites settings.

## 4. Post-deploy verification

Check each with curl or a browser:

- [ ] `/` — **200**, marketing page, with **NO "Swarm Playground" link**
- [ ] `/swarm/` — **404**
- [ ] `/contribute` — **200**
- [ ] `/docs/` — **200**
- [ ] `/docs/okf/` — **200**
- [ ] `/llms.txt` — **200**
- [ ] `/docs/okf/okf-manifest.json` — **200**, JSON
- [ ] `/.well-known/unigrok.json` — **200**
  - **Caveat:** some static hosts refuse dot-folders. If this 404s, the discovery contract is broken — needs a host-level fix, or redeploy the JSON at an alternate path referenced from `llms.txt`.
- [ ] `/api/public/v1/project` — **200**
  - **Caveat:** this is an extensionless file. Verify the host serves it as JSON, or at minimum serves it at all — machine clients reference this exact path.

## 5. After cutover

Once every verification row above passes, complete the remaining operational steps in the private runbook.
