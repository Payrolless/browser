# Feature specification

Each feature is described as behaviour a user can observe. Sources: using Arc, Arc's public help centre and release notes. Release targets:

- **R1**: first public beta, the minimum an Arc user needs to switch on 22 December 2026
- **R2**: parity with what daily Arc users rely on
- **R3**: later

## Window and sidebar

| Feature | Behaviour | Release |
|---|---|---|
| Sidebar tabs | Tabs are listed vertically in a sidebar on the left of the window, with no horizontal tab strip. The address of the current tab sits at the top of the sidebar. | R1 |
| Hide sidebar | A shortcut hides and shows the sidebar. When hidden, moving the pointer to the window edge shows it over the page. | R1 |
| Favourites | A grid of icons at the top of the sidebar for the most used sites. Favourites are shared by every Space of a profile. | R1 |
| Pinned tabs | Tabs dragged above a divider stay until removed. Each keeps its home address; a shortcut sends a pinned tab back to it. | R1 |
| Today tabs | Tabs below the divider. Each one is archived on its own after a delay the user picks (12 hours, 24 hours, 7 days, 30 days), unless it is pinned. | R1 |
| Archive | Archived tabs stay searchable and can be restored. | R1 |
| Folders | Pinned tabs can be grouped into folders, nested, renamed and collapsed. | R1 |
| Clean up | A button closes or groups today's tabs at once. | R2 |
| Compact top bar | An option shows the address in a thin bar above the page. | R2 |

## Spaces and profiles

| Feature | Behaviour | Release |
|---|---|---|
| Spaces | Each Space has its own pinned and today tabs, a name, an icon and a colour theme. Users switch Space with a swipe, a shortcut or a click on its icon at the bottom of the sidebar. | R1 |
| Space themes | A colour, a gradient or a light/dark mode per Space, applied to the sidebar and window frame. | R1 |
| Profiles | A Space can use its own browser profile: separate cookies, logins, history and extensions. | R1 |
| Link routing | Rules send links opened from other apps to a chosen Space, by domain or by source app. | R2 |

## Command bar and navigation

| Feature | Behaviour | Release |
|---|---|---|
| Command bar | One shortcut opens a centred box that searches open tabs, history, bookmarks, and the web, and runs browser commands by name. | R1 |
| Tab search | The command bar finds an open tab in any Space and switches to it. | R1 |
| Copy link | One shortcut copies the current address. | R1 |
| Find in page | Usual find, with match count. | R1 |

## Viewing several pages

| Feature | Behaviour | Release |
|---|---|---|
| Split view | Two to four tabs side by side in one window, resizable. A split is kept as a single item in the sidebar. | R1 |
| Quick window | A small separate window for a link opened from another app or a shortcut. It can be promoted to a normal tab in a chosen Space. | R1 |
| Peek | A link opened from a pinned tab opens in a floating preview above it, closed with Escape or turned into a tab. | R2 |
| Picture in picture | A playing video moves to a floating player when the user leaves its tab. | R2 |
| Media controls | The sidebar shows play/pause for any tab playing sound. | R2 |

## Customising sites

| Feature | Behaviour | Release |
|---|---|---|
| Site styles | Per-site custom CSS and JavaScript the user writes and toggles, kept with the profile. | R2 |
| Hide elements | Click an element of a page to hide it on that site for good. | R2 |
| Built-in content blocker | Blocks ads and trackers from public filter lists. | R2 |

## Notes and capture

| Feature | Behaviour | Release |
|---|---|---|
| Notes | Plain rich-text notes stored as sidebar items. | R3 |
| Capture | Select an area of a page and copy or save it as an image. | R2 |
| Canvas | A free board mixing captures, links and text. | R3 |

## No AI features

Arc's users came for its power-user workflow, not for AI, and its AI successor Dia lost them. This browser ships no AI features and never sends page content to a model.

## Data and accounts

| Feature | Behaviour | Release |
|---|---|---|
| Import from Arc | Reads the user's own Arc data on the same computer: Spaces, pinned tabs, folders, favourites, plus passwords, history and bookmarks through the Chromium importer. | R1 |
| Import from other browsers | Chrome, Brave, Edge, Firefox, Safari through the Chromium importer. | R1 |
| Chrome extensions | Installs extensions from the Chrome Web Store, with toolbar access from the sidebar. | R1 |
| Password manager | Chromium's built-in password manager, plus extension-based managers. | R1 |
| Sync | Optional, end-to-end encrypted sync of Spaces and pinned tabs across computers, with a self-hostable server. | R3 |
| No account required | The browser works fully without signing in. | R1 |

## Platforms

| Platform | Release |
|---|---|
| macOS 13 or later, Apple silicon | R1 |
| Windows 10 and 11, x64 | R2 |
| Linux x64 | R3 |
| iOS, Android | Not planned |

## Automation

| Feature | Behaviour | Release |
|---|---|---|
| AppleScript | macOS scripts list windows, Spaces and tabs, open and close tabs, and run JavaScript in a tab, so existing Arc scripts can be ported. | R3 |
