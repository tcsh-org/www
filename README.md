# www.tcsh.org

The tcsh website is served by [GitHub Pages][gh-pages] from the [docs
subdirectory of the master branch][docs].  Content is managed using the
[Hugo][hugo] open-source static site generator.

-----

## Updating the site

The general workflow is as follows:

* Use `git clone` to get a copy of the repository.
* Use `git submodule init && git submodule update` to get the theme.
* Use `hugo server -D` to start a local web server.
* Use `vi content/post/announce-6.21.00.md` to edit a file.

Your browser will show the updated content as soon as you save the file.
Keep editing until you are happy with the results.

Commit your changes:

* Commit source changes:
  * Use `git diff` to review source changes.
  * Use `git status` to review new, changed, and removed files.
  * Use `git add` to select files to be committed.
  * Run `git commit` to commit the changes.
* Run `hugo` to regenerate the files in the [docs](docs) directory.
* Commit regenerated files:
  * Use `git diff` to review changes from regenerating the site.
  * Use `git status` to review new, changed, and removed files.
  * Use `git add` to select the regenerated files to be committed.
  * Run `git commit` to commit the regenerated files.
* Merge the two commits and push to GitHub:
  * Run `git rebase -i HEAD~2` and use `fixup` to merge the commits.
  * Run `git push` to push your changes to GitHub.

The source files must be committed before regenerating the site, because
the last-modified timestamp for a source file is derived from its commit
timestamp.

Finally create a pull request to get your changes published.

[Hugo] references:

* [Basic usage of Hugo][hugo-basic]
* [Hugo command line reference][hugo-cli]

[XMin] theme:

* [About Hugo XMin][xmin-about]

### Adding a new page

Create a new file from a template and edit it.

```
hugo new post/announce-6.24.00
vi content/post/announce-6.24.00.md
```

### Removing content

If you are removing content or making other changes that result in
generated content being removed, you must make sure old content is gone.
The easiest way is to simply regenerate everything.

```
rm -rf docs && hugo
```

-----

## Installing Hugo

MacPorts:
```
sudo port install hugo
```

Debian/Ubuntu:
```
apt install hugo
```

NetBSD/SmartOS/others (pkgsrc):
```
pkgin install hugo
```

Or follow the [detailed installation instructions][hugo-install]
from the Hugo documentation.


[docs]: https://github.com/tcsh-org/www/tree/master/docs
[gh-pages]: https://pages.github.com/
[hugo]: https://gohugo.io/
[hugo-basic]: https://gohugo.io/getting-started/usage/
[hugo-cli]: https://gohugo.io/commands/
[hugo-install]: https://gohugo.io/getting-started/installing/
[xmin]: https://xmin.yihui.name/
[xmin-about]: https://xmin.yihui.name/about/
