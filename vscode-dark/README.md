# VS Code Dark for Thunderbird

## 1. Install the theme (colors for the main UI)
1. Zip the **contents** of this folder's `manifest.json` (just that file, at the zip root) and rename it `vscode-dark.xpi`:
   `Compress-Archive manifest.json vscode-dark.zip; Rename-Item vscode-dark.zip vscode-dark.xpi`
2. Thunderbird: **Add-ons and Themes** (Ctrl+Shift+A) > gear icon > **Install Add-on From File...** > pick the `.xpi`.
   (Unsigned add-ons may be refused on Release. Fallback: Add-ons > gear > **Debug Add-ons** > **Load Temporary Add-on** > pick `manifest.json`. That lasts until restart.)
3. Enable "VS Code Dark" under Themes.

## 2. Optional: fine-tuned look (folder pane, message list, buttons, menus)
1. Help > Troubleshooting Information > **Profile Folder: Open Folder**.
2. Create a `chrome` folder there and copy `userChrome.css` and `userContent.css` into it.
3. **Enable the preference below. Without it Thunderbird silently ignores both CSS files** (the theme itself still works, so it is easy to miss).
   - Either: Settings > General > Config Editor (scroll to the bottom of General): set `toolkit.legacyUserProfileCustomizations.stylesheets` = **true**.
   - Or: create a file `user.js` in the profile folder (next to the `chrome` folder) with this line, while Thunderbird is closed:
     `user_pref("toolkit.legacyUserProfileCustomizations.stylesheets", true);`
4. Restart Thunderbird.

Palette: #1f1f1f editor / #181818 sidebar / #2b2b2b borders / #0078d4 accent / #cccccc text (VS Code Dark Modern).
Thunderbird's internal selectors change between versions, so some rules in userChrome.css may need adjusting.

## Window frame looks wrong (orange or colored title bar)?
Windows 11 can tint Thunderbird's title bar and window borders with your accent color while the window is active, which makes text unreadable. Turn it off:
**Settings > Personalization > Colors > Accent color > "Show accent color on title bars and window borders": OFF.**
