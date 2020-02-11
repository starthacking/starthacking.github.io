---
layout: page
title: Contributing
permalink: /contributing.html
---

[StartHacking.org][starthacking] is a [community effort][contributors], and we greatly
appreciate contributions of all kinds.

The easiest way to contribute is through [content requests](#content-requests) or
[bug reports](#bug-reports). Describe what you want or what went wrong!

If you want to contribute content, first [open an issue][issue] describing
your addition to get early feedback on the content that you are adding.
This will also help avoid wasted / duplicate efforts and ensure that
your work is incorporated into the website.

You can also read about the [site setup](#setup), how to [build the
site](#building), our [development workflow](#development-workflow),
and how to submit a [patch](#patches).

### Content Requests

Is there something you wish existed on StartHacking.org?
Please describe it in a [content request][issue] by creating an
[issue](issue-guide).

### Bug Reports

Did you see something wrong on StartHacking.org? Sorry about that! Bug reports
are greatly appreciated.

When you [submit a bug report][issue], please include relevant information such
as the page you were on and what exactly was wrong.

## Development

### Setup

StartHacking.org uses [Jekyll][jekyll], a static site generator.

All the content is written in [Markdown][markdown] files with [Liquid][liquid]
templating (the stuff enclosed in `{}`) and [YAML front-matter][yaml] (the
stuff enclosed in `---` at the top).

To start, clone this repository and change directories.

```bash
git clone git@github.com:starthacking/starthacking.github.io.git
cd starthacking.github.io
```

### Building

To build and run StartHacking.org on your own computer, first [install
Ruby][ruby], then [bundler][bundler], then run the following inside the
`starthacking.github.io` folder:

Run `bundle install` to fetch and install dependencies.

Run `bundle exec jekyll build` to build the site (into the `_site` directory).

For development purposes, it's helpful to run `bundle exec jekyll serve
--watch`. This will watch the source for changes, rebuild when necessary, and
serve the site at `http://localhost:4000`.

### Workflow

When working on a new feature, [branch][help-branch] off `master`. Pull
requests are merged in using non-fast-forward merges using `git merge --no-ff`.

The `master` branch is the live version of the site that is available at
[https://starthacking.org](https://starthacking.org).

### Patches

We love it when people submit new content to StartHacking.org! Start by
[forking][fork] StartHacking.org, then add some content, then submit a [pull
request][help-pr].

When submitting a pull request, your version history should be clean, and
your commit messages should be descriptive and [properly
formatted][commit-message-formatting].

### Style

This project uses [EditorConfig][editorconfig] to make it easier to maintain
a consistent code style. We highly recommend that you use the plugin.

[Plugin for: [Sublime][ec-sublime], [Vim][ec-vim], [Emacs][ec-emacs],
[Atom][ec-atom], [Other][editorconfig]]

There are other conventions (such as 80-column lines) that are not captured
in the EditorConfig. In addition, please try your best to maintain
consistency with the rest of the project in terms of formatting, writing
style, and coding style.

If you have any questions about anything, feel free to open an [issue][issue]
asking for help or ask over [email][email].

[issue]: https://github.com/starthacking/starthacking.github.io/issues
[fork]: https://github.com/starthacking/starthacking.github.io/fork
[editorconfig]: http://editorconfig.org/
[commit-message-formatting]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[email]: mailto:team@hackmit.org
[jekyll]: http://jekyllrb.com/
[ruby]: https://www.ruby-lang.org/en/documentation/installation/
[bundler]: http://bundler.io/
[contributors]: README.md#contributors
[starthacking]: http://starthacking.org
[issue-guide]: https://guides.github.com/features/issues/
[markdown]: https://guides.github.com/features/mastering-markdown/
[liquid]: https://shopify.github.io/liquid/basics/introduction/
[yaml]: https://jekyllrb.com/docs/frontmatter/
[help-pr]: https://help.github.com/articles/using-pull-requests/
[help-branch]: https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell
[ec-sublime]: https://github.com/sindresorhus/editorconfig-sublime#readme
[ec-vim]: https://github.com/editorconfig/editorconfig-vim#readme
[ec-emacs]: https://github.com/editorconfig/editorconfig-emacs#readme
[ec-atom]: https://github.com/sindresorhus/atom-editorconfig#readme

<!--
A good chunk of this guide came from Dotbot's contributing guide:
https://github.com/anishathalye/dotbot/blob/master/CONTRIBUTING.md
-->
