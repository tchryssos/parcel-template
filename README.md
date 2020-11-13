# Troy's Parcel Template

## Setup

1. clone the repo
1. `npm install`
1. edit the meta properties
   - name, version, description, and author in package.json
   - title and meta description in app.html
   - change the favicon in the static folder

## Running Locally

There are 2 ways to run the app locally:

- `npm run dev`
- `npm run prod`

`dev` uses `Parcel`'s development config (with their internal dev server and hot reloading) while `prod` builds a production build of the app and serves that. `dev` is what should be used for regular development, `prod` should be used to check for things like lighthouse score and anything else that would change depending on production optimizations.

## Development

This template uses [`Prettier`](https://prettier.io/docs/en/index.html) and the `.prettierrc` file to maintain style and consistency. If you want to use it, make sure your editor has its respective `Prettier` plugin installed and set to format on save. There is also an `.eslintrc` file to catch things not covered by `Prettier`. Feel free to change the rules in one or both of these `.rc` files, or remove them all together.

## Deploying

The deploy
