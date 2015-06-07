#Setting up Rails to use jsTree on Heroku

##Aims
To setup Rails 4.2 with the assett pipeline to use [jsTree](https://github.com/vakata/jstree) and deploy to Heroku. The setup should allow the full use of [SASS](https://sass-lang.com). No precompiling of assets is required before pushing to Heroku.

##Dependencies
Uses Ruby 2.2.2, Rails 4.2 and jsTree 3.1.1

[Figaro](https://github.com/laserlemon/figaro) is used to set environment variables on Heroku without revealing secrets on public repositories.
Although a database connection is not necessary, the setup for PostgreSql has been left in.

##Explanation
Download [jsTree](https://github.com/vakata/jstree). All the files you need are in the dist folder of the download.
###Javascript

Copy jstree.js to vendor/assets/javascripts.
To `app/assets/javascripts/application.js` add:
```
//= require jstree 
```
###CSS
Rename 