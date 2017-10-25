This is a spike on blogging using GitHub pages.

# Local Test

* Install [jekyll](http://jekyllrb.com/):

  ```bash
  gem install
  ```

* Run jekyll

  ```
  jekyll serve --baseurl ''
  ```

  See [jekyllrb.com/docs/github-pages](http://jekyllrb.com/docs/github-pages/) for details.

* Open [http://localhost:4000/](http://localhost:4000/) in your browser.

Whenever you change one of the files, jekyll will re-generate the site in `_site`. GitHub does the same when we push the repo. Thus, there is no need to check `_site` into git.
