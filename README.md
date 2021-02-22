# ruby.org.vn

The `ruby.org.vn` site is a static site hosted with Github Pages.

* Content is in `/pages` as Haml templates
* Styles are `/stylesheets`, compiled using compass

## How to Contribute

Want to help? Sweet! We like help. Pull requests are very welcome. Here's how
to get started:

1. Fork the repository
2. Make some changes (see _Build Instructions_ below)
3. Push your changes to your fork
4. Open a pull request

When you open a pull request, we'd appreciate if you follow some basic
guidelines:

* Describe what you're changing, and more importantly _why_ you're changing it
* Keep the pull request focused on one thing - if you make two different,
  unrelated changes, please separate them into two pull requests
* Some pull requests won't get merged. All changes are reviewed by a committee
  member, and sometimes changes don't fit with the organisation's vision.

## Build Instructions

Building and deploying the site is done via rake tasks:

* `rake build:all` (aliased as default) compiles the site into `/site`
* `rake deploy` copies the _committed_ versions of all files in `/site` to the
  root of the `gh-pages` branch

There's a `Guardfile`, which makes development convenient - just run `bundle
exec guard` to have it watch the pages and stylesheets, automatically
rebuilding the site any time you save a file.

As a contributor, your workflow would look something like this:

```
# Assuming `upstream` is the name of the git remote for the official
# ruby.org.vn repository, and `origin` is your own fork.

# Make sure you're building on the most up-to-date version
git fetch upstream && git merge upstream/master
# Do some edits
# ...
# If you're not running guard, build the site
rake build:all
# Once you're happy, commit both the source files and the output:
git add pages/my-awesome-page.html.haml
git add site/my-awesome-page.html
git commit -m "Add an awesome page"
# Push your changes
git push origin master
```

## Deploying (for maintainers)

_NOTE_ make sure to have a local branch `gh-pages` tracking `origin/gh-pages`.
This can be accomplished by `git checkout gh-pages`, which on recent versions
of git will automatically setup a tracking branch if there's a remote branch
of the same name.

As a maintainer, your deploy workflow will look something like this:

```
rake build:all
# Check for any changes in 'site'. If there are, read over them, and commit.
git add site
git commit -m "Committing changes to the generated site"
git push origin master

# Update the gh-pages branch and push to github
rake deploy
```

If there were changes in `site`, someone forgot to commit the generated output
from a change they made, or they changed the output by hand. This is generally
not a good situation, but mistakes happen...


## Licence

<a rel="license" href="http://creativecommons.org/licenses/by-nc/3.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-nc/3.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Ruby Vietnam website</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://ruby.org.vn" property="cc:attributionName" rel="cc:attributionURL">Ruby Vietnam</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/3.0/">Creative Commons Attribution-NonCommercial 3.0 Unported License</a>.<br />

## Attribution

Based on Ruby Australia static site at <a href="https://github.com/rubyaustralia/ruby.org.au">github.com/rubyaustralia/ruby.org.au</a>.

## Content licence

Content is Copyright 2014-2016 by Ruby Vietnam, All rights reserved.

## Logotype licence

"Ruby Vietnam" 'Gem Dialogue' and Typographic logo are Copyright 2014-2021 by Ruby Vietnam, All rights reserved.
