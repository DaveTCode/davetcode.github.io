# Dave T's Blog

The code backing https://blog.davetcode.co.uk

## Local development

Clone with `git clone --recurse-submodules`, or run `git submodule update --init --recursive` after cloning, to initialise PaperMod at `themes/PaperMod`.

The VS Code devcontainer uses the current Ubuntu base and Hugo 0.168.0 extended, matching CI. Rebuild the container after changing its Dockerfile.

Run `hugo server --bind 0.0.0.0` inside the devcontainer and open http://localhost:1313. Port 1313 is forwarded automatically.

To preview with Podman from PowerShell:

```powershell
podman build -f .devcontainer/Dockerfile -t localhost/davetcode-hugo .devcontainer
podman run --rm -p 127.0.0.1:1313:1313 --mount "type=bind,source=$PWD,target=/workspace,readonly" -e HUGO_RESOURCEDIR=/tmp/hugo-resources -w /workspace localhost/davetcode-hugo hugo server --bind 0.0.0.0 --baseURL http://localhost:1313/ --noBuildLock --destination /tmp/hugo-public --cacheDir /tmp/hugo-cache
```

On Windows, Podman's VM port forwarding must work for the preview to be reachable. If it does not, run `hugo server` directly on Windows with Hugo 0.168.0 extended; container builds can still be tested independently.

## Theme

PaperMod is pinned as a Git submodule. Theme upgrades should be built and checked before committing the updated submodule revision.

Existing `img-lazy` shortcodes use native browser lazy loading and preserve the original image proportions; the former placeholder-ratio argument is retained for compatibility. Site-level PaperMod extension hooks retain the web manifest and article licence notices. Post URLs remain `/post/<filename>/`.

## Deployment

Pushes to the main branch run `hugo --minify` and push the results to the `gh-pages` branch on GitHub, served at https://blog.davetcode.co.uk.