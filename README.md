# COMP0016-T32 Main Website

Welcome, this is team 32 of MotionInput v3.2.

## How to see the generated website

If there is `_site` directory, it is the generated website which is also uploaded to the UCL server.

## How to run the blog in local

1. Install Ruby and NodeJS

This site is built with [Jekyll](https://jekyllrb.com/), a static site generator. To run the site locally, you need to install Ruby and RubyGems first. Then, install Jekyll and Bundler gems through the command line.

```bash
gem install jekyll bundler
```

Next, in the root directory, run:

```bash
bundle install
```

Finally, run the following command in the root directory of the project to start the server.

```bash
bundle exec jekyll serve
```

or to generate a website run:

```bash
bundle exec jekyll build
```

There will be `_site` directory generated in the root directory.

**However**, notice that the website is designed to be deployed in the web server, so the styling will look cracked when opening `index.html` in the browser directly. This is obvious, so please either visit the [website](https://students.cs.ucl.ac.uk/2022/group32/) or run the local server by running `bundle exec jekyll serve`.

## How to write a blog post

To write a post, find the markdown file that you need to write on in the root directory. For example, if you want to put some content in the requirement section, please find `requirements.md` in the root directory.
