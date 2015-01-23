# Contributing

StartHacking.org is a community effort, and we greatly appreciate contributions
of all kinds.

For someone unfamiliar with technical matters, the best way to contribute is
through [content requests](#content-requests) or [bug reports](#bug-reports).

If you would like to author new content, awesome! You can read about the [site
setup](#setup), learn how to [build the site](#building), read about our
[development workflow](#development-workflow), or submit a [patch](#patches).

## Content Requests

Do you have an idea for content that you wish existed on StartHacking.org?
Please [submit a content request][issue].

## Bug Reports

Did you see something wrong on StartHacking.org? Sorry about that! Bug reports
are greatly appreciated!

When you [submit a bug report][issue], please include relevant information such
as the page you were on and what exactly was wrong.

### Setup

StartHacking.org uses [Jekyll][jekyll], a simple static site generator.

All the content is written in Markdown files with Liquid templating, sometimes
with YAML front-matter. It's pretty self-explanatory, and it's very simple to
start editing and authoring content.

### Building

It's very easy build and run StartHacking.org on your own computer.

Run `bundle install` to fetch and install dependencies.

Run `bundle exec jekyll build` to build the site (into the `_site` directory).

For development purposes, it can also be helpful to run `bundle exec jekyll
serve --watch`. This will watch the source for changes, rebuild when necessary,
and serve the site at `http://localhost:4000`.

### Development Workflow

We have a fairly simple development workflow. When working on a new feature,
branch off `develop`. Pull requests are merged in using non-fast-forward merges
using `git merge --no-ff`.

The `master` branch represents the live version of the site. New work should
not branch off `master`.

## Patches

We love it when people submit new content to StartHacking.org! Start by
[forking][fork] StartHacking.org, then add some content, and submit a pull
request.

Before working on substantial changes, it's *highly recommended* that you first
[open an issue][issue] describing your addition to get early feedback on the
content that you are adding. This will also help avoid wasted / duplicate
efforts and ensure that your work is incorporated into the website.

### Style

This project uses [EditorConfig][editorconfig] to make it easier to maintain a
consistent style. We highly recommend that you use the plugin. In addition,
there are other conventions (such as 80-column lines) that are not captured in
the EditorConfig.

In addition, please try your best to maintain consistency with the rest of the
project in terms of formatting, writing style, and coding style.

### Submitting

**Patches must be submitted as pull requests.** For help, see [this
document][help-pr].

When submitting a pull request, your version history should be clean, and your
commit messages should be descriptive and [properly
formatted][commit-message-formatting].

If you have any questions about anything, feel free to open an issue asking for
help or ask over [email][email].

[issue]: https://github.com/starthacking/starthacking.github.io/issues
[fork]: https://github.com/starthacking/starthacking.github.io/fork
[editorconfig]: http://editorconfig.org/
[help-pr]: https://help.github.com/articles/creating-a-pull-request/
[commit-message-formatting]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[email]: mailto:me@anishathalye.com
[jekyll]: http://jekyllrb.com/

<!--
A good chunk of this guide came from Dotbot's contributing guide:
https://github.com/anishathalye/dotbot/blob/master/CONTRIBUTING.md
-->
