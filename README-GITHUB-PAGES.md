# GitHub Pages Configuration

There should be no need to adjust the GitHub configuration. This
documents the configuration for posterity and troubleshooting.

## Set publishing source

There are three choices for the publishing source. We are using the
[master branch /docs folder][gh-pages-pub-source] option. This is
the *document root* of the website.

## Set custom domain name

The website is using https://www.tcsh.org/ as its canonical address.
The custom domain is set using a [CNAME](static/CNAME) file.

[A custom domain name could also be set from the GitHub web
interface][gh-pages-cname] but that just edits the CNAME file in the
*document root*, which would get overwritten when regenerating the site.

## Enable HTTPS

[HTTPS is enabled from the GitHub web interface][gh-pages-https] and
only works for the canonical address https://www.tcsh.org/. Trying to
access https://tcsh.org/ results in an SSL certificate validation error
on the browser.

## HTTP redirects

Typing just `tcsh.org` or `www.tcsh.org` in the browser address bar
works. You will be redirected to https://www.tcsh.org/ from both.

Note that [redirects for custom domains][gh-pages-redirect] only work
over HTTP.


# DNS configuration

The DNS data has a [www CNAME][gh-pages-dns-cname] for `www.tcsh.org`
and [A records][gh-pages-dns-a] for `tcsh.org`.


[gh-pages-cname]: https://help.github.com/en/articles/adding-or-removing-a-custom-domain-for-your-github-pages-site
[gh-pages-dns-a]: https://help.github.com/en/articles/troubleshooting-custom-domains#dns-configuration-errors
[gh-pages-dns-cname]: https://help.github.com/en/articles/setting-up-a-www-subdomain
[gh-pages-https]: https://help.github.com/en/articles/securing-your-github-pages-site-with-https
[gh-pages-pub-source]: https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages#publishing-your-github-pages-site-from-a-docs-folder-on-your-master-branch
[gh-pages-redirect]: https://help.github.com/en/articles/custom-domain-redirects-for-github-pages-sites
