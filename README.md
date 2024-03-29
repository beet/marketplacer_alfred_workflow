# Marketplacer Alfred Workflow

Alfred workflow for automating Marketplacer related actions that are performed on a regular basis throughout the day.

Using workflows with Alfred requires a paid license, but if you don't already own it, please ask your friendly neighbourhood manager :)

## Default settings

Some of the actions will prompt you to select values from a list, such as the Github repository or project, but default values can be set using the Alfred's workflow environment variables.

To customise the Alfred workflow environment variables, click the weird `[x]` icon in the top right.

* `default_project_id`: if you do most of your work on one kanban board, like Bauhaus for example, grab the ID from its URL like https://github.com/orgs/marketplacer/projects/18 and enter `18` to use that board by default without prompting you
* `default_repository`: if the Github isses you work on are primarily under one repository, like `marketplacer`, set this var to use that repo by default

## Actions summary

Github actions:

* `misssues` - **m**arketplacer **i**ssues
* `mio` + number - **m**arketplacer **i**ssue **o**pen
* `miu` + number - **m**arketplacer **i**ssue **u**rl
* `mim` + number - **m**arketplacer **i**ssue **m**arkdown
* `mipp` + issue number + issue title - **m**arketplacer **i**ssue **p**roject **p**age
* `mprv` + number - **m**arketplacer **p**ull **r**equest **v**iew
* `mpru` + number - **m**arketplacer **p**ull **r**equest **u**rl
* `mprm` + number - **m**arketplacer **p**ull **r**equest **m**arkdown
* `mprfsha` - **m**arketplacer **P**R **f**or **SHA**
* `mnb` + branch name: construct conformant branch name
* `mcm` + commit subject: construct conformant commit message subject
* `mblame` + path/to/file.rb:123 - open git blame view on GitHub

Tettra actions:

* `mtes` + search phrase - **m**arketplacer **te**ttra **s**earch

Trello actions:

* `mtro` - **m**arketplacer **tr**ello **o**pen

MCP actions:

* `mcpvs` - **mcp** **v**ertical **s**earch

DataDog actions:

* `mdog` - open ECS dashboard in DataDog

Sidekiq actions:

* `msid` - open M Connect Sidekiq dashboard

Flipper actions:

* `mflip` - open M Connect Flipper dashboard


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

### Generate issue project page

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

#### Obsidian tasks integration

The next actions section will include sections for due today and overdue:


    ### Due today

    ```tasks
    not done
    due today
    path includes Issue {var:issue_id} - {var:issue_title}
    ```

    ### Overdue

    ```tasks
    not done
    due before today
    path includes Issue {var:issue_id} - {var:issue_title}
    ```

This requires the [obsidian-tasks](https://github.com/schemar/obsidian-tasks) plugin for [Obsidian](https://obsidian.md/)

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

### Construct conformant branch name

`mnb` + branch name string _(with spaces, will be converted)_. 

Requires the `git_name` workflow environment variable to be set.

Automates the process of constructing a conformant branch name by prompting for a contentional commit type, and converting the input into snake case.

![pic](docs/mnb_start.png)

Pick a type:

![pic](docs/mnb_type.png)

Pastes `my.name/feat/my_awesome_branch` into the front most app.

### Construct conformant commit message subject

Automates the process of constructing a conformant commit message _subject_ by providing a select list for the commit type, and then further prompting for a commit scope when the type requires it.

![pic](docs/mcm_start.png)

Pick a type:

![pic](docs/mnb_type.png)

If the type requires a scope, pick from the list:

![pic](docs/mcm_scope.png)


Pastes `feat(seller): add an amazing new feature` into the front most app.

### Open blame view in GitHub

`mblame` + path/to/file.rb:123

Open git blame view on GitHub, where a little blue icon provides "View blame prior to this change"

Useful for code archaeology when the last commit on a line is from a linter to find the _previous_ change that may provide insights into its intent.

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

## Datadog actions

![datadog](docs/datadog.png)

### Open Datadog dashboard

* Keyword: `mdog`, yo

Opens the [ECS dashboard in Datadog](https://app.datadoghq.com/dashboard/wua-naq-h2w/christians-ecs-overview?tpl_var_application=integrations&from_ts=1643929744318&to_ts=1644534544318&live=true).

## Sidekiq actions

![sidekiq](docs/sidekiq.png)

### Open Sidekiq dashboard


* Keyword: `msid`

Prompts to open either the M Connection production Sidekiq dashboard, or the `test-bart` Sidekiq dashboard.

## Flipper actions

![flipper](docs/flipper.png)

### Open Flipper dashboard

* Keyword: `mflip`

Opens the M Connect Flipper feature flag dashboard.
