# Welcome
### Stack
#### Styling
- UnoCSS
- Daisyui
- Flowbite
#### Core
- Remix
#### Deployment
- Cloudflare Workers
#### Database
- D1 (Alpha - Testing alternatives also)
- KV (maybe)
- DO (maybe)
#### Testing 
- Playwright
- Github Actions

## Development

You will be running two processes during development:

- The Miniflare server (miniflare is a local environment for Cloudflare Workers)
- The Remix development server

Both are started with one command:

```sh
pnpm run dev
```

Open up [http://127.0.0.1:8787](http://127.0.0.1:8787) and you should be ready to go!

If you want to check the production build, you can stop the dev server and run following commands:

```sh
pnpm run build
pnpm start
```

Then refresh the same URL in your browser (no live reload for production builds).

## Deployment

If you don't already have an account, then [create a cloudflare account here](https://dash.cloudflare.com/sign-up) and after verifying your email address with Cloudflare, go to your dashboard and set up your free custom Cloudflare Workers subdomain.

Once that's done, you should be able to deploy your app:

```sh
pnpm run deploy
```

# Dependencies
Dependencies integrated at remix project
[example repo](https://github.com/remix-run/examples/tree/main/unocss)

# Remix + UnoCSS

UnoCSS is the instant, on-demand atomic CSS engine. It has various advantages over Tailwind CSS. Read more in the [GitHub readme](https://github.com/unocss/unocss).

## Preview

Open this example on [CodeSandbox](https://codesandbox.com):

[![Open in CodeSandbox](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/github/remix-run/examples/tree/main/unocss)

## Example

This example shows a bare-bones setup of UnoCSS.

List of dependencies installed:

- `unocss`
- `@unocss/reset`
- `@unocss/cli`

The `scripts` in [`package.json`](./package.json) have been updated to use the UnoCSS CLI to generate CSS into `app/styles/uno.css`. This file is imported to [`app/root.tsx`](./app/root.tsx) to apply these styles into the Remix app. A Tailwind CSS preset is also being used from `@unocss/reset` to add basic global styles according to Tailwind CSS defaults.

You can add more presets in [`unocss.config.ts`](./unocss.config.ts).

## Related Links

- [UnoCSS GitHub](https://github.com/unocss/unocss)
- [UnoCSS Docs](https://uno.antfu.me)

# Throbleshooting
## End of Space 
Error: ENOSPC: System limit for number of file watchers reached, watch '/home/raul/dev/remix/apps/remix/unocss.config.ts'

```bash
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p
```
P.S. The ideal is to investigate the cause (probabily some watch mode reading the node_modules, and should be set to igore it)

