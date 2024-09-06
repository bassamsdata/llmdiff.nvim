# llmdiff.nvim

`llmdiff.nvim` is a Neovim plugin that integrates with the [mini.diff](https://github.com/echasnovski/mini.diff) plugin to manage and display differences between the original buffer content and modifications made by a LLM using [codecompanion.nvim](https://github.com/olimorris/codecompanion.nvim) plugin. It automatically switches between showing diffs based on the LLM output or Git changes, and provides features to revert or update these changes.

## Features

- Automatically switches the diff source to show changes made by an LLM during inline editing.
- Reverts the diff back to Git after a configurable delay.
- Provides commands to manually switch between LLM and Git diff sources.
- Supports manual simulation of LLM modifications for testing purposes.

## Installation

To install `llmdiff.nvim` using [lazy.nvim](https://github.com/folke/lazy.nvim), add the following to your plugin configuration:

```lua
return {
  "bassamsdata/llmdiff.nvim",
  event = "VeryLazy",
  dependencies = "echasnovski/mini.diff", -- or "echasnovski/mini.nvim"
  config = function()
    require("llmdiff").setup({
      revert_delay = 5 * 60 * 1000, -- 5 minutes (adjust as needed)
    })
  end,
}
```

## Usage

`llmdiff.nvim` automatically activates during inline editing with LLM. You can also manually trigger some of its functionalities:

- `require("llmdiff").force_codecompanion()`: Force the plugin to switch to the LLM diff.
- `require("llmdiff").force_git()`: Revert back to the Git diff source.
- `require("llmdiff").simulate_llm_modification()`: Simulate an LLM modification for testing.


## Thanks

Special thanks to the following amazing plugins:

- [codecompanion.nvim](https://github.com/olimorris/codecompanion.nvim) by [olimorris](https://github.com/olimorris) for enabling seamless integration of LLM-based inline edits into Neovim.
- [mini.diff](https://github.com/echasnovski/mini.diff) by [echasnovski](https://github.com/echasnovski) for providing a lightweight and flexible diffing solution.

Their work has been invaluable. 

