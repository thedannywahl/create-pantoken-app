# create-pantoken-app

Serves the `create-pantoken-app` agent skill at `https://create.pantoken.app`. `/` is a redirect
stub (meta-refresh + `location.replace`) pointing at `/SKILL.md`, the canonical raw copy — a
plain-text `.html` root previously confused agent fetch tools that ran the page through an
HTML-to-text conversion pass and mangled the embedded markdown.

`404.html` is a third, raw copy of the skill: GitHub Pages serves it for any unmatched path
(including `/`, since there's no Jekyll `permalink` processing — this repo is `.nojekyll`), so a
plain non-rendering `GET /` still gets the content immediately instead of the redirect stub. It has
the same downsides the redirect fixes for `index.html` — `.html`-typed body some fetch tools mangle,
and an HTTP 404 status some tools refuse to read the body of — so it's a fallback, not the primary
path.

`SKILL.md`, `index.html`, and `404.html` are generated from
[`ai/pantoken-ai/skills/create-pantoken-app/SKILL.md`](https://github.com/thedannywahl/pantoken/blob/main/ai/pantoken-ai/skills/create-pantoken-app/SKILL.md)
in the `pantoken` repo — don't hand-edit them here. `llms.txt` and `.well-known/api-catalog` are
hand-maintained in this submodule instead: `llms.txt` is an agent-legible index of this site (the
[`llms.txt`](https://llmstxt.org/) convention), and `.well-known/api-catalog` is an
[RFC 9727](https://www.rfc-editor.org/rfc/rfc9727.html) linkset pointing agents at `SKILL.md` as the
service doc. To publish an update to the generated files, in the `pantoken` repo:

```sh
vp exec node docs/scripts/stage-create-pantoken-app-domain.ts
cd ai/create-pantoken-app-site
git commit -am "sync create-pantoken-app skill"
git push
```

GitHub Pages redeploys automatically on push to `main`.
