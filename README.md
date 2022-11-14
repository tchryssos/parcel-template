# Troy's Parcel Template

[Parcel](https://parceljs.org/getting_started.html)

## Setup

1. clone the repo
1. run `yarn`
1. edit the meta properties
   - name, version, description, author, and potentially the `deploy` command(s) in `package.json`
   - title and meta description in `index.html`
   - change the favicon in the static folder

## Running Locally

There are 2 ways to run the app locally:

- `yarn dev`
- `yarn prod`

`dev` uses `Parcel`'s development config (with their internal dev server and hot reloading) while `prod` builds a production build of the app and serves that. `dev` is what should be used for regular development, `prod` should be used to check for things like lighthouse score and anything else that would change depending on production optimizations.

`dev` hosts to `localhost:1234` while `prod` hosts to `localhost:1235` so that both can be run simultaneously.

## Development

This template uses [`Prettier`](https://prettier.io/docs/en/index.html) and [`eslint`](https://eslint.org/) to maintain style and consistency. For best results, make sure your editor has its respective `Prettier` and `eslint` plugins installed and set to format on save. The `.vscode` folder included with this repo _should_ set this up automatically for you, but if you aren't using vscode you'll need to set that up yourself.
