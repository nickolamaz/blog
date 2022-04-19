This repo uses the [Minimal Mistakes Jekyll theme](https://github.com/mmistakes/minimal-mistakes). [Configure as necessary](https://mmistakes.github.io/minimal-mistakes/docs/configuration/).

## Writing a Blog Post

Make a Markdown file named `YYYY-MM-DD-unique-title-slug-here.md` in the `_posts` directory. Posts
should have a metadata header like this one (see existing posts for more examples):

```
---
title: "A Guide to Kubernetes Chargeback"
description: "Learn how to successfully implement a showback or chargeback strategy for Kubernetes."
date: 2021-08-03T8:00:00-04:00
canonical_url: "https://blog.kubecost.com/blog/kubernetes-chargeback"
classes: wide
categories:
  - blog
tags:
  - Chargebacks
  - Monitoring
---
```

Write your posts in normal Markdown. If you need images, put them in `assets/images` and link them
in the Markdown.

If you'd like to attribute the post to an author, add an entry to `_data/authors.yml` with a name (e.g. `Foo Bar`) and then add `author: Foo Bar` to the metadata header section of the post. If you don't want to attribute it, leave off the `author:` field and it will be authored by Kubecost.

If you need a captioned image, the Jekyll theme we use requires this syntax (instead of the default Markdown). See the [official docs](https://mmistakes.github.io/minimal-mistakes/docs/helpers/#figure).

``` sh
{% include figure image_path="/assets/images/yourimage.png" alt="Image alt text" caption="Image caption" %}
```


## Testing Locally

### MacOS

Make sure you have [RVM](https://rvm.io/) installed:
```
curl -sSL https://get.rvm.io | bash -s stable
```

Then run this command to get a local instance of the blog at [http://localhost:4000](http://localhost:4000):
```sh
bash --login -c 'rvm install 2.7.3 && \
    rvm use 2.7.3 && \
    gem install bundler && \
    bundle install && \
    bundle exec jekyll serve'
```


### Generic

Make sure you have Ruby 2.7 installed (GitHub pages apparently doesn't work with Ruby 3.0 as of 2021-08-24).

Install `bundle`
``` sh
gem install bundler
```

Install necessary Gems

``` sh
bundle install
```

Run a local version of the site:
``` sh
bundle exec jekyll serve
```

See the theme's documentation for other questions.


---

## Troubleshooting

If you have a question about using Jekyll, start a discussion on the [Jekyll Forum](https://talk.jekyllrb.com/) or [StackOverflow](https://stackoverflow.com/questions/tagged/jekyll). Other resources:

- [Ruby 101](https://jekyllrb.com/docs/ruby-101/)
- [Setting up a Jekyll site with GitHub Pages](https://jekyllrb.com/docs/github-pages/)
- [Configuring GitHub Metadata](https://github.com/jekyll/github-metadata/blob/master/docs/configuration.md#configuration) to work properly when developing locally and avoid `No GitHub API authentication could be found. Some fields may be missing or have incorrect data.` warnings.
