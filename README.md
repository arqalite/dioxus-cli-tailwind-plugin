# Tailwind CSS for Dioxus
Tailwind CSS plugin for [Dioxus CLI]. Currenly a very early WIP.

## Goals
* Download Tailwind automatically on first run, making sure it downloads the right executable for your OS
* On first run, generate default config files without overwriting existing ones.
* Regenerate CSS on each reload
    * Currently it's bugged and the CLI and plugin are causing each other to reload repeatedly. This is a known issue and will be fixed soon.

## Usage
The plugin system is still in development, so these steps will change frequently and will cover only new projects. A guide to migrate existing projects will be added once the plugin system is finalized and released.

For now, you will first need to install @arqalite's fork of Dioxus CLI which patches a file download issue:

```bash
cargo install --git https://github.com/arqalite/dioxus-cli
```

Once installed, you can create a new project and initialize the plugin system:

```bash
dioxus create <project-name>
cd <project-name>
dioxus plugin init
```

Now we can finally install the plugin:

```bash
dioxus plugin add --git https://github.com/DioxusPluginCommunity/tailwind-plugin
```
<strong>NOTE: Notice the lack of a trailing slash at the end - if you include it the plugin will not install. Bug in CLI.</strong>

Run `dioxus plugin list` to make sure it's installed correctly. The plugin should initialize and start downloading Tailwind and add two default config files to your project (src/tailwind.config.js and src/input.css).

Last step - open Dioxus.toml and add "public/style.css" as shown below:

```toml
# CSS style file
style = ["style.css"]
```

We should be good to go! Run `dioxus serve` and you should see Tailwind CSS working. As you change any *.rs files, the plugin will automatically regenerate the CSS file as the server reloads.
It will reload probably 5 times every time you make a change, but it works. :)

## Contributing
All contributions are welcome! Please feel free to open an issue or a pull request.
## License
This project is licensed under the [MIT license](https://github.com/DioxusPluginCommunity/tailwind-plugin/blob/main/LICENSE).

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in Rummy Nights, shall be licensed as MIT, without any additional
terms or conditions. We reserve the right to reject contributions that will not be licensed as such.

[Dioxus CLI]: https://github.com/DioxusLabs/cli
[Tailwind CLI]: https://github.com/tailwindlabs/tailwindcss/releases 
