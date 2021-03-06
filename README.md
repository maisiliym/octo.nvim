# octo.nvim
Plugin to work with GitHub issues and PRs from Neovim. Just edit the issue description/comments and save it with `:w`.
Modified description or comments are highlighted in the signcolumn.


![](https://i.imgur.com/pv9MSJW.png)


## Installation

Use your favourite plugin manager to install it. eg:

```
Plug 'pwntester/octo.nvim'
```

## Requirements

- Install [GitHub CLI](https://cli.github.com/)
- Install [telescope.nvim](https://github.com/nvim-telescope/telescope.nvim) for using the `ListXXX` commands which enables to fuzzy pick issues from a dropdown menu.

```
Plug 'nvim-lua/popup.nvim'
Plug 'nvim-lua/plenary.nvim'
Plug 'nvim-telescope/telescope.nvim'
```


## Commands

| Object | Action | Arguments|
|--------|--------|--------|
| issue | close | |
| | open | |
| | create | [repo] |
| | edit | [repo] <number> |
| | list | [repo] [key=value]*<br>[Available keys](https://cli.github.com/manual/gh_issue_list): `author`\|`assignee`\|`mention`\|`label`\|`milestone`\|`state`\|`limit`<br>Mappings:<br>`<CR>`: Edit issue<br>`<C-t>`: Opens issue in web browser |
| pr | list | [repo] [key=value]*<br>[Available keys](https://cli.github.com/manual/gh_pr_list):  `assignee`\|`label`\|`state`\|`base`\|`limit`<br>Mappings:<br>`<CR>`: Edit PR<br>`<C-t>`: Opens PR in web browser<br>`<C-o>`: Checkout PR |
| gist | list | [repo] [key=value]*<br>[Available keys](https://cli.github.com/manual/gh_gist_list):  `repo`\|`public`\|`secret`<br>Mappings:<br>`<CR>`: Append Gist to buffer<br>`<C-t>`: Opens Gist in web browser |
| comment | add | |
| | delete | |
| label | add | <label> |
| | delete | <label> |
| assignees| add | <assignee> |
| | delete | <assignee> |
| reviewer | add | <reviewer> |
| | delete | <reviewer> |
| reaction | add | <+1\|-1\|eyes\|laugh\|confused\|rocket\|hooray>|
| | delete | <+1\|-1\|eyes\|laugh\|confused\|rocket\|hooray>|

* If repo is not provided, it will be derived from `<cwd>/.git/config`.

## Usage

Just edit the issue title, description or comments as a regular buffer and use `:w(rite)` to sync the issue with GitHub.

## Completion

`<C-x><C-o>`: When cursor is located at text that matches `#\d*` will popup a list of repo issues starting with the same id prefix.

## Mappings

`<Plug>(GoToIssue)` can be used to navigate to a local repo issue. By default mapped to `gi` but can be overriden with: 

```
nmap gi <Plug>(GoToIssue)
```

## Highlight groups

| Name | Default |
------------------
|`OctoNvimDirty`|`ErrorMsg` |
|`OctoNvimCommentHeading`|`PreProc`|
|`OctoNvimCommentUser`|`Underlined`|
|`OctoNvimIssueTitle`|`PreProc`|
|`OctoNvimIssueId`|`Question`|
|`OctoNvimIssueOpen`|`MoreMsg`|
|`OctoNvimIssueClosed`|`ErrorMsg`|
|`OctoNvimEmpty`|`Comment`|
|`OctoNvimFloat`|`NormalNC`|

## TODO

- [ ] autocompletion for @person

## Credits
All `List` commands are taken from @windwp [Telescope extension](https://github.com/nvim-telescope/telescope-github.nvim) and adapted to edit issues.
