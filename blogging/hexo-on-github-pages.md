# Static Website Hexo on GitHub

It's easy to setup a Hexo website, there are tons of tutorials on the internet.

## Hexo: Basic Setup

It's easy to setup a Hexo website, there are tons of tutorials on the internet.

```
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```

You'll need several useful plugins to improve your Hexo website, such as to generate RSS feed and XML sitemap.

## Push your Hexo website to GitHub

How to use GitHub Pages to host your website for free? Just create a new GitHub Repository. It's free if the repository is public.

Then Install ``hexo-deployer-git`` plugin:

```
$ npm install hexo-deployer-git --save
```

Edit the setting:

```
deploy:
  type: git
  repo: <repository url>
  branch: [branch]
  message: [message]
```

Try to ``hexo deploy`` to deploy it to your repository.

Notice that GitHub Pages will build and serve website from one of the branch such as ``gh-pages`` or ``master``. So you have to set ``source`` in repository settings.

## Use HTTPS

Cloudflare provides free SSL to secure your website, all you have to do is:

* Visit ``Crypto`` section in your domain name dashboard
* In the first panel SSL, turn it on. The option should be "Flexible" or "Full"
* Make sure your domain name is fully managed by Cloudflare

## Auto Deployment using CircleCI

* Add ``circle.yml`` in your repository.
```
checkout:
  post:
    - git submodule sync
    - git submodule update --init

deployment:
  production:
    branch: master
    commands:
      - git config --global user.name "Circle CI"
      - git config --global user.email "YOUR EMAIL HERE"
      - hexo clean
      - hexo generate
      - hexo deploy

test:
  override:
    - echo "Passed"
```
* In CircleCI, add your project and let it try to build your website.
* Remember to sync submodule if you use submodule to clone a theme into your repository.
* You can use something like ``html-proofer`` to validate the HTML and find out dead links. However I choose to ``echo "Passed"``.
* You have to generate a pair of SSH key and add it to CircleCI SSH Permission so that CircleCI will be able to access to your GitHub repository for both ``read and write``.

Once the settings are done, the publishing process will be much easier: create a new post and commit it into your repository.
