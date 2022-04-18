<p align='center'>
  <img src="https://github.com/LuisAlejandro/send-tweet-with-media/blob/develop/branding/banner.svg">
  <h3 align="center">Send tweet with media</h3>
  <p align="center">GitHub Action for tweeting with images</p>
</p>

---

Current version: 0.1.0

## 🎒 Prep Work

1. Create an app with the twitter account where you want to share the tweets (https://developer.twitter.com/apps). You might need to fill an application form before being able to create an app. More info [here](https://github.com/gr2m/twitter-together/blob/main/docs/01-create-twitter-app.md).
2. Upload your images to a public access URL.

## Workflow Usage

Configure your workflow to use `LuisAlejandro/send-tweet-with-media@v0.1.0`,
and provide the tweet you want to send as the `STATUS_TEXT` env variable.

You can add up to 4 images as URLs in `STATUS_IMAGE_URL_1`,
`STATUS_IMAGE_URL_2`, `STATUS_IMAGE_URL_3` and `STATUS_IMAGE_URL_4`
env variables. The script will download and attach them to the tweet.

Provide the authentication keys and tokens for your Twitter app
as the `TWITTER_CONSUMER_KEY`, `TWITTER_CONSUMER_SECRET`,
`TWITTER_OAUTH_TOKEN`, and `TWITTER_OAUTH_SECRET` env variables
(as secrets). Remember, to add secrets go to your repository
`Settings` > `Secrets` > `Actions` > `New repository secret`
for each secret.

For example, create a file `.github/workflows/push.yml` on
a github repository.

```yml
name: Send a Tweet
on: [push]
jobs:
  tweet:
    runs-on: ubuntu-20.04
    steps:
      - uses: LuisAlejandro/send-tweet-with-media@v0.1.0
        env:
          TWITTER_CONSUMER_KEY: ${{ secrets.TWITTER_CONSUMER_KEY }}
          TWITTER_CONSUMER_SECRET: ${{ secrets.TWITTER_CONSUMER_SECRET }}
          TWITTER_OAUTH_TOKEN: ${{ secrets.TWITTER_OAUTH_TOKEN }}
          TWITTER_OAUTH_SECRET: ${{ secrets.TWITTER_OAUTH_SECRET }}
          STATUS_TEXT: "Hi! I'm tweeting from Github actions using https://github.com/LuisAlejandro/send-tweet-with-media"
          STATUS_IMAGE_URL_1: https://picsum.photos/1024/768
          STATUS_IMAGE_URL_2: https://picsum.photos/1024/768
          STATUS_IMAGE_URL_3: https://picsum.photos/1024/768
          STATUS_IMAGE_URL_4: https://picsum.photos/1024/768
```

## 🕵🏾 Hacking suggestions

- You can test the script locally with Docker Compose:

  * Install [Docker Community Edition](https://docs.docker.com/install/#supported-platforms) according with your operating system
  * Install [Docker Compose](https://docs.docker.com/compose/install/) according with your operating system.

      - [Linux](https://docs.docker.com/compose/install/#install-compose-on-linux-systems)
      - [Mac](https://docs.docker.com/compose/install/#install-compose-on-macos)
      - [Windows](https://docs.docker.com/compose/install/#install-compose-on-windows-desktop-systems)

  * Install a git client.
  * Fork this repo.
  * Clone your fork of the repository into your local computer.
  * Open a terminal and navigate to the newly created folder.
  * Change to the `develop` branch.

          git branch develop

  * Create a `.env` file with the content of the environment secrets as variables, like this (with real values):

          STATUS_TEXT=xxxx
          STATUS_IMAGE_URL_1=xxxx
          STATUS_IMAGE_URL_2=xxxx
          STATUS_IMAGE_URL_3=xxxx
          STATUS_IMAGE_URL_4=xxxx
          TWITTER_CONSUMER_KEY=xxxx
          TWITTER_CONSUMER_SECRET=xxxx
          TWITTER_OAUTH_TOKEN=xxxx
          TWITTER_OAUTH_SECRET=xxxx

  * Execute the following command to create the docker image (first time only):

          make image

  * You can execute the tweet script with this command:

          make tweet

  * Or, alternatively, open a console where you can manually execute the script and debug any errors:

          make console
          python3 entrypoint.py

  * You can stop the docker container with:
  
          make stop

  * Or, destroy it completely:
  
          make destroy
  

## Made with :heart: and :hamburger:

![Banner](https://github.com/LuisAlejandro/send-tweet-with-media/blob/develop/branding/author-banner.svg)

> Web [luisalejandro.org](http://luisalejandro.org/) · GitHub [@LuisAlejandro](https://github.com/LuisAlejandro) · Twitter [@LuisAlejandro](https://twitter.com/LuisAlejandro)