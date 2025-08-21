# misskey-themes

My collection of custom Misskey themes. I keep them here so I can version, tweak, and share easily. If you want a clean Twitter-like look with orange accents, you’ll probably like these.

## What’s inside

- __`twitter black orange pure.txt`__
  - Name: Twitter Pure Dark (Orange)
  - Base: `dark`
  - Goal: pure black background with subtle panels and orange accent.

- __`twitter white orange pure.txt`__
  - Name: Twitter Pure Light (Orange)
  - Base: `light`
  - Goal: clean white/light UI with the same orange accent.

Both files use Misskey’s theme format (supports variables like `@accent` and functions like `:darken<10<...`). One file uses a more JS-like object style (unquoted keys/single quotes); the other is strict JSON-y. Misskey handles both when pasted into the theme editor.

## How to use (import into Misskey)

I usually import by pasting the theme JSON directly:

1. Open your Misskey instance and log in.
2. Go to: Settings → Appearance → Themes.
3. Choose “Create new theme” or “Import” (depending on your instance wording).
4. Open one of the files in this repo and copy the entire contents.
5. Paste into the theme editor/import modal.
6. Save/apply. If your instance supports previews, you’ll see it immediately.

If your instance only supports file import:

- Download the `.txt` file you want and import it as a theme file. Misskey reads the contents and applies it the same way as pasting.

## Customizing

I structure themes around a few core props you can safely tweak:

- __`accent`__ – the brand color. Change this hex to recolor the whole theme.
- __`bg` / `fg`__ – background and foreground (text) base colors.
- __`panel` / `panelHeader*`__ – timeline cards, sidebars, and headers.
- __`divider` / `shadow`__ – subtle details that affect depth and borders.
- __`link` / `hashtag` / `mention`__ – link-like elements.

Misskey’s theme DSL supports:

- __Variable references__: `@accent`, `@fg`, etc.
- __Transforms__: `:lighten<amount<@var`, `:darken<amount<@var`, `:alpha<opacity<@var`.

If you only want a different accent color, update `accent` and Misskey will propagate that through the references. For example, in these themes I use `#d97706` (orange) and then compute `accentDarken`, `accentLighten`, `accentedBg`, etc.

## Notes on the two variants

- __Dark variant__ aims for true black backgrounds (`#000`) for OLED-friendly contrast, with panels slightly lightened and low-contrast dividers.
- __Light variant__ uses a clean white base with gentle panel darkening and soft shadows to keep it readable without heavy borders.

Both variants keep the same semantics so switching between them feels consistent.

## File structure

```
./
├─ twitter black orange pure.txt   # dark theme object
├─ twitter white orange pure.txt   # light theme object
└─ README.md
```

## Troubleshooting

- __Paste/import errors__: Make sure you copied the whole file, including the opening `{` and closing `}`. If your instance complains about quotes, try the other file (the light variant is fully quoted). You can also swap single quotes for double quotes if needed.
- __Theme not applying__: After saving, reload the page or clear cached theme if your instance has that option.
- __Low contrast or unreadable text__: Tweak `fg`, `panel`, and `divider` a bit. Small changes (±2–5 in `:lighten`/`:darken`) go a long way.

## Contributing

If you have ideas or want adjustments for other accent colors, feel free to open an issue or a PR with a new file (follow the same structure and naming). Keep props consistent so themes stay easy to compare.

## Roadmap

- More accent presets (blue, teal, purple).
- Optional higher-contrast variants.
- Optional compact spacing variant.

## Credits

Built on Misskey’s theme system. All color math uses the built-in theme DSL (`@var`, `:lighten`, `:darken`, `:alpha`).
