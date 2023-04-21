# Instructions on publishing the website

## Webcontent

The first thing is to locate yourself into website-content folder via 

```shell
cd ~/Dropbox/git/website-content/my-site
```

Then you may edit the contents in the `content` forder.
* `page` is for any miscellanous pages
* `posts` is for blog posts

## Hugo build

Before publish the website, you may want to take a look at you website, you may do so via 

```shell
hugo server 
```

Then it will provide a localhost which you may preview your website. If everything is fine and ready to publish, then under the `my-site` folder, you should type 

```shell
hugo -t hugo-ink
```

where [hugo-ink](https://github.com/knadh/hugo-ink) is the theme I use, and `-t` tell hugo that I will use this theme (this `-t hugo-ink` maybe optional if you only have one theme located in your directory, but I don't know for sure.  
Then all the publish-ready file are located at `./my-site/public` forlder. Notice that the public forder is the local repository of [my website](https://github.com/zhengbo0503/zhengbo0503.github.io). This includes using submodule which described fully [here](https://www.youtube.com/watch?v=LIFvgrRxdt4).

## Publishing

Ready to submit! You should visit `public` forder in your terminal and then do the following

```shell
git add .
git commit -m "update on ..."
git push origin main
```

You may now go to the github repo [here](https://github.com/zhengbo0503/zhengbo0503.github.io), and then you can see the files are all updated. For more information, you may access to [Action](https://github.com/zhengbo0503/zhengbo0503.github.io/actions) to check the workflow. Once in [Action](https://github.com/zhengbo0503/zhengbo0503.github.io/actions), it says "pages build and deployment", then you are good to go, and this build and deploy process usually takes 1 minutes.



