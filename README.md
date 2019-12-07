# www.tcsh.org

The tcsh website is served by [GitHub Pages][gh-pages] from the [docs
subdirectory of the master branch][docs].  Content is managed using the
[Hugo][hugo] open-source static site generator.


## Updating the site

The general workflow is as follows:

* Use `git clone` to get a copy of the repository.
* Use `git submodule init && git submodule update` to get the theme.
* Use `hugo server -D` to start a local web server.
* Use `vi content/post/announce-6.21.00.md` to edit a file.

Your browser will show the updated content as soon as you save the file.
Keep editing until you are happy with the results.

Commit your changes:

* Use `git diff` to review source changes.
* Use `git status` to review new and removed files.
* Use `git add` to select files to be committed.
* Run `git commit` to commit the changes.
* Run `hugo` to regenerate the files in the [docs](docs) directory.
* Run `git add` to select the regenerated files to be committed.
* Run `git commit` to commit the regenerated files.
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
hugo new post/announce-6.21.00
vi content/post/announce-6.21.00.md
```

### Removing content

If you are removing content or making other changes that result in
generated content being removed, you must make sure old content is gone.
The easiest way is to simply regenerate everything.

```
rm -rf docs && hugo
```


## Installing Hugo

MacPorts:
```
sudo port install hugo
```

Debian/Ubuntu:
```
apt-get install hugo
```

NetBSD/SmartOS/others (pkgsrc):
```
pkgin install hugo
```

Or follow the [detailed installation instructions][hugo-install]
from the Hugo documentation.


## GitHub configuration

There should be no need to adjust the GitHub configuration. This
documents the configuration for posterity and troubleshooting.

### Set publishing source

There are three choices for the publishing source. We are using the
[master branch /docs folder][gh-pages-pub-source] option. This is
the *document root* of the website.

### Set custom domain name

The website is using https://www.tcsh.org/ as its canonical address.
The custom domain is set using a [CNAME](static/CNAME) file.

[A custom domain name could also be set from the GitHub web
interface][gh-pages-cname] but that just edits the CNAME file in the
*document root*, which would get overwritten when regenerating the site.

### Enable HTTPS

[HTTPS is enabled from the GitHub web interface][gh-pages-https] and
only works for the canonical address https://www.tcsh.org/. Trying to
access https://tcsh.org/ results in an SSL certificate validation error
on the browser.

### HTTP redirects

Typing just `tcsh.org` or `www.tcsh.org` in the browser address bar
works. You will be redirected to https://www.tcsh.org/ from both.

Note that [redirects for custom domains][gh-pages-redirect] only work
over HTTP.


## DNS configuration

The DNS data has a [www CNAME][gh-pages-dns-cname] for `www.tcsh.org`
and [A records][gh-pages-dns-a] for `tcsh.org`.


## Why not Jekyll?

Managing Ruby dependencies is too difficult. Having everything dumped
inside the global Ruby installation directories is just asking for
trouble.

A reasonable approach might be using [the official Jekyll Docker
image][jekyll-docker] but even that seemed much heavier a setup than I'd
like to impose on anyone working on the content.

Completely foregoing local review of changes in favor of simply having
GitHub Pages regenerate the site &mdash; warts and all &mdash; just
doesn't feel right, does it?


[docs]: https://github.com/tcsh-org/www/tree/master/docs
[gh-pages]: https://pages.github.com/
[gh-pages-cname]: https://help.github.com/en/articles/adding-or-removing-a-custom-domain-for-your-github-pages-site
[gh-pages-dns-a]: https://help.github.com/en/articles/troubleshooting-custom-domains#dns-configuration-errors
[gh-pages-dns-cname]: https://help.github.com/en/articles/setting-up-a-www-subdomain
[gh-pages-https]: https://help.github.com/en/articles/securing-your-github-pages-site-with-https
[gh-pages-pub-source]: https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages#publishing-your-github-pages-site-from-a-docs-folder-on-your-master-branch
[gh-pages-redirect]: https://help.github.com/en/articles/custom-domain-redirects-for-github-pages-sites
[hugo]: https://gohugo.io/
[hugo-basic]: https://gohugo.io/getting-started/usage/
[hugo-cli]: https://gohugo.io/commands/
[hugo-install]: https://gohugo.io/getting-started/installing/
[jekyll-docker]: https://hub.docker.com/r/jekyll/jekyll/
[xmin]: https://xmin.yihui.name/
[xmin-about]: https://xmin.yihui.name/about/
