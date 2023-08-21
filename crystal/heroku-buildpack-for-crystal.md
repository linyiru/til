# Heroku Buildpack for Crystal

In a Crystal-based project, initialize your heroku app:

```
heroku create --buildpack https://github.com/crystal-lang/heroku-buildpack-crystal.git
```

If you want to assign the heroku app name:

```
heroku create YOUR_APP_NAME --buildpack https://github.com/crystal-lang/heroku-buildpack-crystal.git
```

Deploy to heroku:

```
git push heroku master
```

Open the website/application:

```
heroku open
```
