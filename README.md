# Troy's Parcel Template

## Setup

1. clone the repo
1. `npm install`
1. edit the meta properties
   - name, version, description, author, and potentially the `deploy` command(s) in `package.json`
   - title and meta description in `index.html`
   - change the favicon in the static folder

## Running Locally

There are 2 ways to run the app locally:

- `npm run dev`
- `npm run prod`

`dev` uses `Parcel`'s development config (with their internal dev server and hot reloading) while `prod` builds a production build of the app and serves that. `dev` is what should be used for regular development, `prod` should be used to check for things like lighthouse score and anything else that would change depending on production optimizations.

## Development

This template uses [`Prettier`](https://prettier.io/docs/en/index.html) and the `.prettierrc` file to maintain style and consistency. If you want to use it, make sure your editor has its respective `Prettier` plugin installed and set to format on save. There is also an `.eslintrc` file to catch things not covered by `Prettier`. Feel free to change the rules in one or both of these `.rc` files, or remove them all together.

The intended organization of this template is as follows:

- JS code should be organized into various files under the `logic` folder (which is aliased as `logic` within the repo, so if you need to access a file `src/logic/elements`, you can import from `logic/elements`). I generally have the following files in addition to ones specific to the project:
  - `elements` for html element references
  - `util` for helper functions (`clamp`, `getRandomNumber`, etc)
  - `contants` for constants
  - `state` if there is any stateful logic. Each piece of "state" is broken down into a `let`, an exported getter, and an exported setter. Never direclty manipulate or read your `let`.
- JS code in the `logic` folder is imported into the `main.js` file for execution. If I'm making an app to draw silly faces the functions to draw the faces might be written in `src/logic/faces`, imported into `src/main`, and then executed. `main.js` is the only file that is imported into the html file.
- Styles belong in the `styles` folder. By default, only `main.css` is imported into the html file, but I often break my styles down into multiple sheets and add imports. NOTE: There are currently no css scoping tools in this project, so either add something like [`cssmodules`](https://github.com/css-modules/css-modules) or use a naming convention like [BEM](http://getbem.com/naming/) (or just be careful about naming) to prevent style name collisions as the number of style files in your app expands.
- Static files go in the `src/static` folder. This folder is aliased as `static`.
- There is an `index.html` file included, but feel free to create more if you want.

File path aliasing is done in `package.json` under the `alias` key. `static` and `logic` are already aliased, so if you want to add more aliases, just copy those examples. You can read more about how `Parcel` handles aliasing [here](https://parceljs.org/module_resolution.html)

## Deploying

By default, this template assumes you're going to be deploying to github pages. If you plan on using custom hosting, you'll need to update the `deploy` command to fit your setup. If, however, you're cool with using github pages, read on.

There are two `deploy` commands in this repo. `deploy:only_first` should only be used the FIRST TIME you deploy. Subsequent deploys should use the `deploy` command.

The `deploy` command combines information from [this gist](https://gist.github.com/cobyism/4730490) and [this blog post](https://clontz.org/blog/2014/05/08/git-subtree-push-for-deployment/). Essentially, we're taking our `main` branch (check this! your default branch might be `master`, in which case you'll need to update the command or your branch name!), copying ONLY the `dist` folder where our build lives (and is created automatically by the command) and pushing that to our `gh-pages` branch, which github knows to automatiaclly deploy to a github pages page.

The reason we need a `deploy:only_first` command is that the `deploy` command will fail if the `gh-pages` branch doesn't exist. `deploy:only_first` creates and pushes this branch, then immediately runs the regular deploy command to overwrite it with the `dist` folder. `deploy:only_first` will also delete your `node_modules` folder and then re-install it, since occassionally `Parcel` will fail to build initially if your `node_modules` folder is out of date. Note that if `deploy:only_first` gets as far as creating and pushing the `gh-pages` branch (which it almost certainly will) and then errors or crashes, you still need to switch to the `deploy` command after you've fixed your errors.

To summarize:

- `npm run deploy:only_first` to deploy the first time
- `npm run deploy` to deploy every subsequent time
