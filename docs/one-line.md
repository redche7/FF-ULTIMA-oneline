# Optional one-line layout

The fork can place the address bar, horizontal tabs and navigation buttons on
one row while retaining Ultima's color schemes. This implementation targets
Firefox 157 with Nova. Appearance refinements are still in progress.

## Enable or disable

Create the boolean `ultima.oneline.enabled` in `about:config` and set it to
`true`. Restart Firefox to reload the stylesheets. A missing or `false` value
leaves ordinary Ultima active.

For a persistent preset, add this line to your profile's `user.js`:

```js
user_pref("ultima.oneline.enabled", true);
```

To disable permanently, change it to `false` or remove it and set the preference
to `false` in `about:config`. A `true` entry in `user.js` reapplies on startup.
One-line is opt-in; the fork's default `user.js` leaves the preference unset.

## Existing Ultima settings

| Preference | Behavior while one-line is active |
| --- | --- |
| `ultima.navbar.hide.buttons` | `true`: reveal buttons together on navigation/tab hover or focus; an open toolbar popup holds them. `false`: keep buttons visible. |
| `ultima.navbar.bookmarks.autohide` | `true`: reveal bookmarks over the page on toolbox hover, keyboard focus or an open folder. Hide the overlay while address suggestions are open. `false`: keep a bookmarks row below the combined row. |
| `ultima.navbar.bookmarks.position` | `left`, `center`, `right`; alignment falls back toward the start when items overflow. |
| `ultima.navbar.bookmarks.compact` | Use Ultima's compact 20px bookmarks height instead of the normal 36px row/overlay. |
| `ultima.disable.windowcontrols.button` | Hide controls in the combined row; retain Ultima's visible-menu-bar control fallback. |

Firefox's own bookmarks visibility still applies. One-line does not reveal a
toolbar hidden through Firefox's toolbar menu. Window density controls the
combined row height; no preference values are changed by CSS.

## Fallbacks

One-line applies to ordinary horizontal-tab windows. Customize Toolbar, vertical
tabs, popup windows and page DOM fullscreen retain Ultima's layout.

The following Ultima combinations also retain their existing layout rather than
activate one-line:

- Navbar autohide, floating/fullsize navbar or a bottom navbar.
- Floating bookmarks or a floating URL bar.
- Hidden/autohiding tab bar.

F11 browser fullscreen is separate from page DOM fullscreen and needs its own
manual check. Prototype feedback so far has been on Windows; Linux/macOS have
not been verified. The current appearance work targets dark mode. Very narrow
windows and precise tab/suggestions appearance remain unfinished.

## Timings and custom styles

The defaults in `theme/one-line/toolbars.css` are:

| Variable | Default |
| --- | --- |
| `--uo-show-delay` | `0.1s` |
| `--uo-show-duration` | `0.3s` |
| `--uo-hide-grace` | `2s` |
| `--uo-hide-duration` | `1.5s` |

Bookmarks use 160ms opacity/slide transitions without a delay. Reduced motion
removes movement/fade durations.

`customChrome.css` and `customContent.css` remain the final user extension
points. To override timing variables without affecting ordinary Ultima, use
this selector in `customChrome.css`:

```css
:root:not([customizing], [inDOMFullscreen], [popup-window], [chromehidden~="toolbar"]):has(#tabbrowser-tabs[orient="horizontal"]) {
  --uo-hide-duration: 1.5s;
}
```

The one-line modules retain MPL-2.0 notices and acknowledge the MIT-licensed
FoxOne layout/reveal ideas in `theme/one-line/FOXONE-LICENSE.txt`.
