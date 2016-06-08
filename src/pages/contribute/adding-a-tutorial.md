---
layout: main.html
---

# Adding a tutorial
The process of adding a tutorial or guide to fuge is very easy. All of our documents are written
in markdown with the ability to mix in HTML as needed too.

Assuming you have a forked of this site. Your tutorial or guide should live in the
[/src/pages/tutorials][] folder.

``` bash
| -- src
  | -- pages
    | -- tutorials
      | -- index.md
      | -- your-tutorial-here.md
```

## Checking how it looks
fuge.io has the ability to run offline. This means you can see how your tutorial looks on the
site before you commit your changes. To run the site locally, simply:

``` bash
npm run start
```

A locally ran version of fuge.io will now be available in your browser at [localhost:8000][].
The local version of the site is hot reload capable. To have your changes reload simply save them
and use the refresh function of your browser to reload the site.

## Linking to your tutorial
When you complete your tutorial you will need to add it to the list of tutorials, which can be
found at [/src/pages/tutorials/index.md][].


## Deploying your changes
fuge.io auto generates itself based on commits to the master branch. This means that as soon as
your PR is accepted your changes will go live. You do not need to take any special action here.

[localhost:8000]: http://localhost:8000/
[/src/pages/tutorials/index.md]: /tutorials/
[/src/pages/tutorials]: /tutorials/