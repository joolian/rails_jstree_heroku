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

Copy `jstree.js` to `vendor/assets/javascripts`.
To `app/assets/javascripts/application.js` add:
```
//= require jstree 
```

###Images
Create a folder in 'assets/images' called `jstree-default` and then copy all the image files from `dist/themes/default` to the new folder.
Repeat the same procedure with the image files from `dist/themes/default-dark`.

###CSS
Copy `dist/themes/default/style.css` to `vendor/assets/stylesheets` and give it a unique name (e.g. `jstree-default.scss`) and change the extension to `.scss`.
Now we need to point all references to image files in the scss file to the images in `assets/images` using the image-url helper.
Change:
```background-image: url("40px.png");```
to:
```background-image: image-url("jstree-default/40px.png");```

If you want to make full use of SASS then replace all the require statements in `assets/stylesheets/application.css` with option statements and change the file extension of `application.css` to `.scss`. Otherwise add require statements for the edited style sheets.
