# wrightster/.github

Org-level defaults for the wrightster organization. Right now that means one
thing: `.github/workflows/laravel-ci.yml`, the reusable CI workflow every
Laravel repo in the fleet calls — laravel_base, baton, invite, and (cross-org)
bullcitylearning's share_links, pulse, expanse, and toolkit. It runs Pint, Pest,
and a blocking `composer audit`; it deploys nothing. Each repo's
`.github/workflows/ci.yml` is a thin caller that supplies the triggers (push,
manual, and a weekly cron so `composer audit` still runs on quiet repos) plus at
most two inputs: `build-assets: true` for apps whose tests render `@vite` views,
`package-mode: true` for the toolkit, which tests through testbench. This repo
is **public** on purpose — a private repo's reusable workflows cannot be called
from another organization, and bullcitylearning's repos are private. The
standard this implements, and the reasoning behind detection-only CI on
Ploi-hosted apps, is `jims_dev_way/playbooks/deployment.md`.
