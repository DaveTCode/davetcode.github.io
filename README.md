# Dave T's Blog

The code backing https://blog.davetcode.co.uk

## Local development

Clone the repo as normal but run `git submodule update --init` to initialise the submodule at ./public.

Run `hugo serve` to have a development server up running. The project has a vscode devcontainer with hugo installed

## Deployment

Pushes to the main branch will run `hugo minify` and push the results to the `gh-pages` branch on github from which they'll be accessible on https://blog.davetcode.co.uk