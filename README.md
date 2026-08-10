# babello.nvim

- [Description](#description)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
  - [Keymaps](#keymaps)
  - [Commands](#commands)
  - [Configuration](#configuration)
- [Contributing](#contributing)
- [License](#license)

## Description

Babel: the Babel's tower

l: the L of [DeepL](https://www.deepl.com/en/translator)

o: Oh wow, this is beautiful OR Oh wow, it surprisingly works!

babello.nvim is a [Neovim](https://neovim.io/) plugin for [Babello](https://github.com/utox39/babello)

## Requirements

- [Babello](https://github.com/utox39/babello)
- A DeepL API Key

## Installation

> [!NOTE]
> This only installs the Neovim plugin. The plugin shells out to the `babello` binary on your `$PATH`, so you need to install [Babello](https://github.com/utox39/babello).

```lua
return {
  {
    "utox39/babello.nvim",
    lazy = false,
    config = function()
      require("babello").setup({
        target_lang = "EN-US",
        -- your other overrides
      })
    end,
  },
}
```

## Usage

`DEEPL_API_KEY` must be set.

Select the text that you want to translate/improve in visual mode, then you have
2 options: use a keymap or a command.

### Keymaps

| Keymap        | Action                                             |
| ------------- | ---------------------------------------------------   |
| `<leader>bt`  | Translate the selection                               |
| `<leader>bT`  | Translate the selection, prompting for a language first |
| `<leader>bI`  | Improve (fix spelling/grammar of) the selection       |

### Commands

| Command | Action |
| ---------------------- | --------------------------------------------------- |
| `:BabelloTranslate` | Translate the selection |
| `:BabelloTranslateAs` | Translate the selection, prompting for a language first |
| `:BabelloImprove` | Improve (fix spelling/grammar of) the selection |
| `:BabelloImproveAs` | Improve the selection, prompting for a language first |

Either one opens a preview window with the result. From there:

| Key           | Action                                  |
| ------------- | ---------------------------------------- |
| `<CR>` or `r` | Replace the selection with the result   |
| `p`           | Paste the result below the selection    |
| `q` or `<Esc>`| Cancel, discarding the result           |

### Configuration

Pass any of these to `require("babello").setup({ ... })` to override the defaults:

```lua
require("babello").setup({
  bin = "babello",                                    -- must be on $PATH
  source_lang = nil,                                  -- nil = auto-detect
  target_lang = "EN-US",
  favorite_languages = { "EN-US", "IT", "DE", "FR" },  -- quick-pick list
  keymaps = {
    translate = "<leader>bt",
    translate_as = "<leader>bT",
    improve = "<leader>bI",
    -- set an entry to false to disable that keymap
  },
  preview = {
    width = 0.6,   -- relative to editor width
    height = 0.4,  -- relative to editor height
    border = "rounded",
  },
})
```

`DEEPL_API_KEY` must be set in the environment Neovim runs in, same as for the CLI.

## Contributing

Please see [CONTIBUTING](https://github.com/utox39/babello.nvim/blob/main/CONTRIBUTING.md). Thanks!

## License

MIT License. See: [LICENSE](https://github.com/utox39/babello.nvim/blob/main/LICENSE)
