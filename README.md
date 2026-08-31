# create-pantoken-app

Serves the `create-pantoken-app` agent skill at `https://create.pantoken.app`. `/` is a redirect
stub (meta-refresh + `location.replace`) pointing at `/create-pantoken-app.md`, which holds the raw
skill content — a plain-text `.html` root previously confused agent fetch tools that ran the page
through an HTML-to-text conversion pass and mangled the embedded markdown.

`index.html` and `create-pantoken-app.md` are generated from
[`ai/pantoken-ai/skills/create-pantoken-app/SKILL.md`](https://github.com/thedannywahl/pantoken/blob/main/ai/pantoken-ai/skills/create-pantoken-app/SKILL.md)
in the `pantoken` repo — don't hand-edit them here. To publish an update, in the `pantoken` repo:

```sh
vp exec node docs/scripts/stage-create-pantoken-app-domain.ts
cd ai/create-pantoken-app-site
git commit -am "sync create-pantoken-app skill"
git push
```

GitHub Pages redeploys automatically on push to `main`.
