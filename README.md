
# 🚧 You are likely looking for [template](https://github.com/distillpub/template) instead. 🚧 [![Build Status](https://travis-ci.org/distillpub/pipeline.svg?branch=master)](https://travis-ci.org/distillpub/pipeline)

This is just infrastructure code to build the `distill.pub` website.

# Build and Deploy the Distill Website

Instructions for how to build and deploy the [http://distill.pub](http://distill.pub) website.

Each article on the website is a `post`, whose contents are stored in an external github repository. The manifest of articles is defined in another [public external repo](https://github.com/distillpub/posts/blob/master/posts.csv). During the build process, each of these posts will be processed to be made ready for publishing. A [crossref](http://www.crossref.org/) xml file will also be inserted into its rendered, public directory.

For urls that are not articles, we have a concept of `pages`. These are located within this repository under the `pages/` directory. Each of these go through the same HTML transformations as articles (minus the crossref insertion), with an additional pass through a mustache template evaluator with a data object containing meta data for each of the `posts`. This is how we create the `index.html`, `rss.xml`, and `archive-info/index.html`.

There are four main commands to know.

- **`yarn initialize`** installs all dependencies, then runs `yarn poll` and `yarn make`.

- **`yarn poll`** Polls github for changes to all post repositories, the `distill-template` repo, and the `distill-posts/posts.csv` manifest file.

- **`yarn make`** Builds the site (without pinging any remote repositories), placing all the output in the `docs/` folder. The `docs/` folder is then served automatically by [github pages](https://help.github.com/articles/configuring-a-publishing-source-for-github-pages/) when the changes are committed and pushed to Github.

- **`yarn build`** will run all the transformations necessary to build the site, specifically `yarn poll` and `yarn build`.

- **`yarn serve`** Starts a static file server to view website. To view the site, navigate to `localhost:8000/docs`.

(The above commands require using `bash`.)

Happy building!
