# create-pantoken-app

Serves the `create-pantoken-app` agent skill at `https://create.pantoken.app`, so an agent CLI can
fetch the domain root directly instead of `pantoken.app/create-pantoken-app.md`.

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
