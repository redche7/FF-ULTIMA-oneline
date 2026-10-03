# One-line settings

Use horizontal tabs and enable Nova (`browser.nova.enabled=true`).

Set the boolean `ultima.oneline.enabled` in `about:config`, then restart Firefox:

- `true`: enable one-line; included in this fork's `user.js` preset.
- `false`: restore ordinary Ultima. A missing preference also leaves it active.

If you keep `user.js` in your profile, update its matching entry too;
otherwise it reapplies the preset at startup.

The preset uses Compact density, disables Windows Mica and sends New Tab
search input to the address bar.

Vertical tabs, Customize Toolbar, popup windows and page fullscreen use ordinary
Ultima. Floating bars, a bottom navbar, navbar autohide or a hidden/autohiding tab
bar also retain Ultima's layout.

With `ultima.navbar.bookmarks.autohide=true`, the bookmarks toolbar appears on
hover over the top toolbars as an overlay above the page, without moving or
resizing its content. This differs from ordinary Ultima's autohide layout,
which changes the space available to the page. Autohide is optional; in one-line
mode, setting it to `false` reserves a normal row for bookmarks.

`ultima.spacing.compact.tabs` does not shrink tabs separately in one-line mode;
it keeps its original behavior in ordinary Ultima.

In one-line mode, the tab counter keeps its label above 1100 CSS px, shows only
the number at narrower widths, and hides at 800 CSS px or less to leave room
for tabs.

For all other settings, see the [Ultima Wiki](https://ff-ultima.github.io/docs/category/theme-settings).

In dark mode, Container Style 3 uses a 50% container-color tint and light text on
the selected tab. This shared styling also applies to ordinary Ultima layouts.
