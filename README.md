# ABW2022
Ascochyta Blight Workshop 2022 website

## Hugo conference template

This conference website repository is based on the [Hugo conference-theme](https://github.com/jweslley/hugo-conference) developed by [Jonhnny Weslley](https://github.com/jweslley) for conferences/events, based on the original [conf-boilerplate theme](https://github.com/braziljs/conf-boilerplate/) by [BrazilJS Foundation](http://braziljs.org/).

You can build the site using standalone [Hugo](https://gohugo.io), or with the R package [blogdown](https://pkgs.rstudio.com/blogdown/) (that handles Hugo setup, site building and serving using R commands and the RStudio interface).

Instructions for getting up and running with either of these options are listed below:  

## Building my conference site from scratch (using Hugo)

1. Install [Hugo](https://gohugo.io)
2. Create a new site by running:

        hugo new site my-conf
        cd my-conf
        git clone https://github.com/jweslley/hugo-conference themes/hugo-conference
        rm -f config.toml
        cp themes/hugo-conference/exampleSite/config.yml .

3. It's done. Just start Hugo server to see it live!

        hugo server --watch

## Building my conference site from scratch (using blogdown)

### TL;DR

Follow these steps to get up and running in no time:

```
# install required packages (you will need to install the 'remotes' package first)
# install.packages('remotes')
remotes::install_github('r-lib/usethis')
remotes::install_github('rstudio/blogdown')
# load required packages
library(usethis)
library(blogdown)
# create a new project and setup git for version control
create_project('path-to-project')
use_git()
use_github()
# create the new site 
new_site(theme = "jweslley/hugo-conference")
file.copy("themes/hugo-conference/exampleSite/config.yml", "config.yaml", overwrite=TRUE)
serve_site()

```

### Detailed instructions 

1. From RStudio, install blogdown using `install.packages('blogdown')` (or the development version with `remotes::install_github('rstudio/blogdown')`)  
2. Create a new project in RStudio (in the _File_ menu), make sure you tick the 'use git for version control' checkbox (alternatively use the functions from `usethis` as described above). 
3. Create the new site with `blogdown::new_site(theme = "jweslley/hugo-conference")`.  
4. Copy the theme config file to the root folder with `file.copy("themes/hugo-conference/exampleSite/config.yml", "config.yaml", overwrite=TRUE)` (note that we changed the file suffix from `.yml` to `.yaml` so it will be recognised by blogdown/Hugo)
5. Serve the site with `blogdown:::serve_site()` (or using the *Serve Site* option under the *Blogdown* section in the *Addins* menu in RStudio)

More about project management and version control in R can be found in the following resources:

* [Structuring R Projects](https://chrisvoncsefalvay.com/2018/08/09/structuring-r-projects/) by Chris von Csefalvay
* [Happy Git and GitHub for the useR](https://happygitwithr.com/index.html) by Jennifer Bryan
* `usethis` R package - see documentation and setup instructions at <https://usethis.r-lib.org/articles/usethis-setup.html>

More about creating websites and blogging with `blogdown` can be found in the excellent [blogdown: Creating Websites with R Markdown](https://bookdown.org/yihui/blogdown/) by Yihui Xie, Amber Thomas, Alison Presmanes Hill, as well as the more updated blog post [Up & running with blogdown in 2021](https://www.apreshill.com/blog/2020-12-new-year-new-blogdown/) by Alison Presmanes Hill (which includes how to host your new site for free on [Netlify](https://www.netlify.com/) or on [GitHub pages](https://pages.github.com/))

## Customizing the site

All the site information can be found in the `config.yaml` file. Just edit it to make changes.
By default, the site have the following sections:

- About - to describe what's the main goal of your event.
- Location - to show where it's going to happen through Google Maps.
- Speakers - to list information about speakers.
- Schedule - to show the agenda.
- Sponsors - to show the brand of your sponsors.
- Partners - to show the brand of your partners.

**PS**, It's important to change the `baseurl` property from `config.yaml` file in order to reflect your settings.

### Google Maps

Google now requires a Google Maps JavaScript API Key to show maps. You can obtain your key [here](https://developers.google.com/maps/documentation/javascript/get-api-key). Then export your API key as an environment variable and point to this variable in the `GoogleMapsKey` param in the `config.yaml` file (see more information about this [here](https://wowchemy.com/docs/hugo-tutorials/security/)).

## Troubleshooting

If Hugo won't start serve your website and complains about version conflict, check that you don't have 2 different versions installed (they are installed on `C:\Users\current-user\AppData\Roaming\Hugo` on a Windows computer). You can check which version is used by blogdown by running `blogdown::hugo_version()` and if there's a conflict, you can specify the correct version in `.Rprofile` in the repository (add the following line: `options(blogdown.hugo.version = "0.92.0")`, as an example, modify as needed based on the version installed in your system).


## License

MIT, see [LICENSE](https://github.com/jweslley/hugo-conference/blob/master/LICENSE).
