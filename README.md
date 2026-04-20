# scandiweb Brand Assets

Static brand asset CDN for the `scandiweb-brand-custom` Claude skill, which generates on-brand Google Slides presentations via the Slides API.

## Structure

- `backgrounds/` — full-bleed slide background images (dark title, separators, gradients, office photo)
- `Icons/` — brand icon library (~115 icons, categorized by prefix: `Arrows_*`, `Finance_*`, `Marketing_and_analytics_*`, etc.)
- `logos/` — scandiweb wordmark in white and red variants

## How this is used

The Claude skill references these files via `raw.githubusercontent.com` URLs pinned to a specific commit SHA. Google Slides' `createImage` API fetches them at deck-insertion time and bakes the image bytes into each presentation.

## Contributing — please read before pushing

- **Do not force-push or rewrite history.** Existing decks reference specific commit SHAs; if those SHAs become unreachable, Google's fetcher will fail and already-built decks stay fine (images are already baked in) but any re-render would break.
- **Do not change filenames.** The skill's asset registry keys map to specific filenames. Renaming a file breaks the registry until the skill is updated.
- **Adding new assets is fine.** Drop new icons/backgrounds in the appropriate folder and they'll be available once the skill's registry is updated to include them.
- **Replacing assets:** commit the replacement under the same filename, then bump `ASSET_REF` in the skill's `references/implementation.md` to the new commit SHA.

## License

All rights reserved. These are scandiweb brand assets; external use is not permitted.
