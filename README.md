# Tabby Next

[![ci](https://github.com/erfur/tabby/actions/workflows/ci.yml/badge.svg?branch=master)](https://github.com/erfur/tabby/actions/workflows/ci.yml)

> **Fork disclaimer:** Tabby Next is an independent fork of [Tabby](https://github.com/Bill13579/tabby). It is not affiliated with or maintained by the original Tabby project or its authors.

Tabby Next is an open-source window and tab manager that can manage large numbers of windows and tabs with ease.

Install a release package from this repository's [GitHub releases](https://github.com/erfur/tabby/releases), or see [Building, Installing, and Editing](#building-installing-and-editing) for development builds.

# Contributing

If you like this project, please share it. Your support is always welcomed!

Tabby Next is open source and independently maintained. Contributions are welcome.

# Building, Installing, and Editing

## Prerequisites

- [Git](https://git-scm.com/)
- [Rustup](https://www.rust-lang.org/tools/install) (rustc >= 1.62.1)
- [wasm-pack](https://rustwasm.github.io/wasm-pack/installer/) >= 0.10.3
- [Node.js](https://nodejs.org/en/) >= 16.15.0 LTS
- Firefox >= 59 (recommended)<br/>
  or<br/>
  Chrome >= 49 (fully tested on Chrome 72)
  
**IMPORTANT NOTE:** If you encounter an issue compiling the "lindera-ipadic" dependency on the `npm run build:firefox` step, it is likely that you do not have enough memory or CPU. This is especially an issue on virtual machines, and is hard to detect since the error messages are incredibly vague.  
On an Ubuntu VM, 4gb RAM + 2 cores has been proven to work.

## Building Tabby Next

1. Open a git enabled shell of your choice (e.g. Command Prompt, Git Bash)
2. Get the source code  
`git clone https://github.com/erfur/tabby.git`
3. Go into the project directory<br/>
`cd tabby`
4. Install dependencies with npm  
`npm install`
5. Build Tabby Next<br/>
Firefox: `npm run build:firefox`  
Chrome: `npm run build:chrome`  
WebExtension: `npm run build:webext`

The `dist` folder, after the build, can then be packaged as a zip file and installed.

## Installation

### Firefox
This will install Tabby Next as a temporary add-on, so you will need to repeat it every time you restart Firefox.

1. Start Firefox
2. Go to `about:debugging`
3. Press on the `Load Temporary Add-on...` button
4. Select the `manifest.json` file in the `dist` directory

### Chrome

1. Start Chrome
2. Go to `chrome://extensions`
3. Press on the `Load unpacked` button
4. Select the `dist` directory

## Publishing Releases

Publishing a GitHub release whose tag matches `v<EXT_VERSION>` builds the Firefox extension, signs it through Mozilla's unlisted AMO channel, and attaches the signed XPI to the release. The repository must define `AMO_JWT_ISSUER` and `AMO_JWT_SECRET` secrets containing AMO API credentials.

## Editing & Testing

After you edit the code, you will need to build again.

Re-do Step 5 of [Building Tabby Next](#building-tabby-next) and<br/>
- on Firefox, press the `Reload` button in the Tabby Next section of the `about:debugging` page.<br/>
- on Chrome, press the <img src="https://i.imgur.com/FcVtjot.png" alt="Chrome Reload Icon" width="23px" /><!-- https://imgur.com/a/VHMbJ4l --> button in the Tabby Next section of the `chrome://extensions` page.

Note: Content Scripts will only be reloaded for each tab once that tab is refreshed.

# File Structure

icons/ - Directory for storing Tabby Next icons<br/>
icons/tabby.svg - Tabby Next icon (Vector)<br/>
icons/tabby.png - Tabby Next icon (Raster)<br/>

release/ - Release zip files<br/>

screenshots/ - Screenshots<br/>
screenshots-archive/ - Old screenshots of old releases<br/>

dist/ - Distribution directory<br/>
src/ - Source code directory (for more info, go to the [README.md](src/README.md) file in that directory)<br/>

LICENSE - License file<br/>
README&#46;md - README file
