# Marketplacer Alfred Workflow

Alfred workflow for automating Marketplacer related actions that are performed on a regular basis throughout the day.

Using workflows with Alfred requires a paid license, but if you don't already own it, please ask your friendly neighbourhood manager :)

## Default settings

Some of the actions will prompt you to select values from a list, such as the Github repository or project, but default values can be set using the Alfred's workflow environment variables.

To customise the Alfred workflow environment variables, click the weird `[x]` icon in the top right.

* `default_project_id`: if you do most of your work on one kanban board, like Bauhaus for example, grab the ID from its URL like https://github.com/orgs/marketplacer/projects/18 and enter `18` to use that board by default without prompting you
* `default_repository`: if the Github isses you work on are primarily under one repository, like `marketplacer`, set this var to use that repo by default

## Actions summary

* `misssues` - **m**arketplacer **i**ssues
* `mio` + number - **m**arketplacer **i**ssue **o**pen
* `miu` + number - **m**arketplacer **i**ssue **u**rl
* `mim` + number - **m**arketplacer **i**ssue **m**arkdown
* `mipp` + issue number + issue title - **m**arketplacer **i**ssue **p**roject **p**age
* `mprv` + number - **m**arketplacer **p**ull **r**equest **v**iew
* `mpru` + number - **m**arketplacer **p**ull **r**equest **u**rl
* `mprm` + number - **m**arketplacer **p**ull **r**equest **m**arkdown
* `mtes` + search phrase - **m**arketplacer **te**ttra **s**earch
* `mtro` - **m**arketplacer **tr**ello **o**pen
* `mprfsha` - **m**arketplacer **P**R **f**or **SHA**
* `mcpvs` - **mcp** **v**ertical **s**earch

## Github actions

These actions may prompt for the project, or use the `default_project_id` workflow setting, and may prompt for the repository, or use the `default_repository` workflow setting.

### Github issues

#### Open issues kanban board

`misssues` - **m**arketplacer **i**ssues

#### Open issue by number

`mio` + number - **m**arketplacer **i**ssue **o**pen

#### Generate issue URL

Constructs a URL, copies it to the clipboard, and pastes it to the front most app.

`miu` + number - **m**arketplacer **i**ssue **u**rl

#### Generate issue Markdown link

Constructs a Markdown link, copies it to the clipboard, and pastes it to the front most app.

`mim` + number - **m**arketplacer **i**ssue **m**arkdown

#### Generate issue project page

`mipp` + issue number + issue title - **m**arketplacer **i**ssue **p**roject **p**age

For each issue I work on, I keep a Markdown project page with links to related resources, next actions, and notes. This action will prompt for the issue number, and then a title for the issue project page. It will then generate a Markdown template and paste it into the front most app, either prompting for the repository or using the workflow default setting:

```markdown
# Issue 123 - Issue title

Tags: #issues

## Resources

* [Issue 123](https://github.com/marketplacer/marketplacer/issues/123)

## Logbook

* **22 Oct 2020:** start

## Next actions

- [ ] Do something

## Notes


```

### Pull requests
 
 These actions will prompt for the repository, or use the `default_repository` workflow setting.

#### View PR in browser

`mprv` + number - **m**arketplacer **p**ull **r**equest **v**iew

#### Generate PR URL

Constructs a URL, copies it to the clipboard, and pastes it to the front most app.

`mpru` + number - **m**arketplacer **p**ull **r**equest **u**rl

#### Generate PR Markdown link

Constructs a Markdown link, copies it to the clipboard, and pastes it to the front most app.

`mprm` + number - **m**arketplacer **p**ull **r**equest **m**arkdown

#### Find the pull request for a given commit SHA

This is a workflow I use almost daily following the principle of "search first, ask questions later". The commit history for me is most useful for tracing a piece of work back to the pull request which should describe the changes in enough detail to get a better understanding of them, ideally also linking to the Github issue and other documentation assets.

Quite often, that's enough to answer the "why" if not _how_ something works.

* Use `git blame` or `git log` to identify a recent commit in the piece of code in question
* Copy the commit SHA
* Enter the `mprfsha` keyword into Alfred, and paste in the SHA
* It will search your selected repo for the SHA, and should reveal the pull request that it came in with

## Tettra actions

### Search Tettra

`mtes` + search phrase - **m**arketplacer **te**ttra **s**earch

## Trello actions

### Open Trello board

Will prompt for the board to open.

`mtro` - **m**arketplacer **tr**ello **o**pen

## MCP actions

Marketplacer Control Panel

### Search for verticals

Enter a phrase to search MCP for verticals:

`mcpvs` - **mcp** **v**ertical **s**earch
