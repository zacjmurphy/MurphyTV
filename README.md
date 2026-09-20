> [!NOTE]
> This theme is heavily based off of [Elegantfin](https://github.com/lscambo13/ElegantFin) by [lscambo13](https://github.com/lscambo13) and the [Elegantfin Jellyfin v12 soft fork](https://github.com/mihaif7/elegantfin-jf12) by [mihaif7](https://github.com/mihaif7). All credit for the original code goes to the original authors.

> [!CAUTION]
> ***This theme is provided as is.** There is no guarantee that this theme will work for you. **Use at your own risk.** Support will be provided by me on a case-by-case basis when I have the available time. Exceptions can be made. **By using this theme you accept these terms.***

# MurphyTV
My personal Jellyfin theme.

## Install
Add the following to your custom css section on Jellyfin.

Paste into **Dashboard → General → Custom CSS** (server-wide) or
**Settings → Display → Custom CSS** (just you):

```css
/* Main ElegantFin CSS */
@import url('https://cdn.jsdelivr.net/gh/lscambo13/ElegantFin@main/Theme/ElegantFin-jellyfin-theme-build-latest-minified.css');

/* ElegantFin Media Bar CSS */
@import url('https://cdn.jsdelivr.net/gh/lscambo13/ElegantFin@main/Theme/assets/add-ons/media-bar-plugin-support-latest-min.css');

/* MurphyTV Companion CSS */
@import url('https://cdn.jsdelivr.net/gh/zacjmurphy/MurphyTV@main/theme/MurphyTV-latest.css');
```

If you'd rather not import from a URL, paste the contents of
[`MurphyTV-latest.css`](theme/MurphyTV-latest.css)
in place of that third line.

## Add-ons

Optional sheets that load **after** the main one. Import none of them and
nothing changes.

```css
/* Classic navbar: the server button as a library pill, as it was before v26.09.18 */
@import url("https://cdn.jsdelivr.net/gh/zacjmurphy/MurphyTV@main/theme/assets/add-ons/classic-navbar-latest.css");
```

| Add-on | What it does |
|---|---|
| `classic-navbar` | Puts the app bar's server button back to a library pill: the fill, the 400 weight, the glyph-sized mark and the pills' hover it had before v26.09.18 made a masthead of it. |

## Supported plugins

Plugins this sheet styles for the Modern layout:

- [Media Bar](https://github.com/IAmParadox27/jellyfin-plugin-media-bar), with or without ElegantFin's Media Bar add-on
- [Media Bar Enhanced](https://github.com/CodeDevMLH/jellyfin-plugin-media-bar-enhanced), with or without ElegantFin's Media Bar add-on
- [Jellyfin Enhanced](https://github.com/n00bcodr/Jellyfin-Enhanced)
- [InPlayerEpisodePreview](https://github.com/Namo2/InPlayerEpisodePreview)
- [Plugin Update Notifier](https://github.com/mihaif7/jellyfin-plugin-update-notifier)
- [Jellyfin Episodes Ratings Grid](https://github.com/Damocles-fr/jellyfin-imdb-episodes-heatmap-ratings-grid), loaded through the [JavaScript Injector](https://github.com/n00bcodr/Jellyfin-JavaScript-Injector)

## Updating

The URL above tracks the newest release, so updates arrive on their own, but
your browser caches the file for up to a week, so **hard-refresh** to pull one
in sooner. What changed in each version is on the
[releases page](https://github.com/zacjmurphy/MurphyTV/releases).

To pin a version instead, name it in the URL. It will then never change:

```css
@import url('https://cdn.jsdelivr.net/gh/zacjmurphy/MurphyTV@v1.0.0/theme/MurphyTV-v1.0.0.css');
```

## Tuning

Override any of these in your own Custom CSS, after the imports:

```css
:root {
    --murphyTV-appBarHeight: 3.5rem;
    --murphyTV-navPillBackground: none;
}
```

| Variable | Default | What it does |
|---|---|---|
| `--murphyTV-appBarHeight` | `4rem` | App bar height |
| `--murphyTV-appBarHeightDesktop` | `4.5rem` | App bar height, desktop layout only |
| `--murphyTV-libraryToolbarHeight` | `3.75rem` | Secondary toolbar on library pages |
| `--murphyTV-libraryToolbarGap` | `0.75rem` | Space under the wrapped toolbar row on mobile |
| `--murphyTV-appBarFade` | `2.5rem` | How far the bar's fill carries below itself when scrolled; `0` for a hard edge |
| `--murphyTV-navRadius` | `1rem` | Library nav button corners |
| `--murphyTV-navPaddingInline` | `1.1rem` | Horizontal room inside the nav pills |
| `--murphyTV-navGap` | `0.6rem` | Gap between adjacent nav pills |
| `--murphyTV-navPillBackground` | `--darkerGradientPointAlpha` | `none` for flat nav buttons |
| `--murphyTV-iconButtonGap` | `0.58rem` | Gap between header icon buttons |
| `--murphyTV-appBarIconSize` | `1.25rem` | App bar icon glyph size |
| `--murphyTV-surfaceRadius` | `1rem` | Menu / popover / dialog corners |
| `--murphyTV-surfaceBlur` | `--blurDefault` | Blur behind menus and dialogs; `none` to disable |
| `--murphyTV-menuGap` | `0.5rem` | Space between a dropdown and the control that opened it |
| `--murphyTV-userMenuFontSize` | `1.15rem` | Avatar menu type on narrow viewports, where MUI holds the rows at 48px |
| `--murphyTV-osdToolbarHeight` | `5rem` | Toolbar height inside the video OSD header |
| `--murphyTV-episodePreviewIcon` | `"video_library"` | Glyph for the in-player episode picker |
| `--murphyTV-linkMarkHeight` | `1.4cap` | Logo mark height in the external-links row |
| `--murphyTV-mediaBarHeight` | `62vh` | Media Bar only: bar height, and what the home sections clear |
| `--murphyTV-mediaBarGap` | `1.25rem` | Media Bar only: the gap above and below the bar |
| `--murphyTV-itemBarEnter` | `0.35s` | How long an item page's app bar takes to fade up to home's background on scroll |
| `--murphyTV-ratingsGridOpen` | `0.24s` | Episodes Ratings Grid only: how long its card takes to unfold; `0s` for no animation |

Upstream ElegantFin's own knobs still work too, including the solid and fully
transparent app bar presets from its README.

## Compatibility

- Jellyfin **12.0**, Modern layout, desktop and mobile.
- ElegantFin **v26.09.05** or later.
- Safe to leave installed on Legacy, everything structural is scoped with
  `:has(.MuiAppBar-root)`, which only matches the Modern layout.
- Non-dark colour schemes fall back to ElegantFin's dark tokens, as they do
  upstream.

If content sits far down the page under a large gap, or buttons come out
indigo, this sheet isn't loading last. Check the import order.

## Credits

[ElegantFin](https://github.com/lscambo13/ElegantFin) by
[lscambo13](https://github.com/lscambo13) - If you like the design go and thank them for the effort :)

[GPL-2.0](LICENSE), matching upstream.