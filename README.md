# David Tomczyk's Personal Site

<!-- TODO: set up git repo (and action to deploy!) -->
<!-- TODO: look into this, but when i deploy i might need/want to purge the cloudflare cache: https://dash.cloudflare.com/832859148f146e8beb31f52450f51344/davidtom.dev/caching/configuration (see API docs) -->
<!-- TODO: review theme features: https://themes.gohugo.io/themes/hugo-sustain/#features
in particular, make sure I set up config correctly: https://github.com/suyundukov/hugo-sustain/blob/master/exampleSite/config.toml
-->
<!-- TODO: set up favicon and other site metadata -->
<!-- TODO: add analytics/tracking to site - SIMPLE: https://github.com/suyundukov/hugo-sustain#google-analytics -->
<!-- TODO: add link to my medium blog to site; WAIT SHOULD I MAKE THIS MY BLOG!? -->
<!-- TODO: write a medium blog for setting up this site!! -->
<!-- TODO: add navigation (see TODO in hugo.toml) -->

# Development

```
hugo serve
```

# Production

See Hugo Deploy instructions for GCS [here](https://gohugo.io/hosting-and-deployment/hugo-deploy/)

## Bucket Set Up

[Bucket settings source](https://qualityandinnovation.com/2020/12/23/pushing-your-hugo-site-to-a-gcs-bucket-part-3/)
[Domain configuration source](https://gist.github.com/p10rahulm/5d23f58ceca389a99594dde52849b381)
[Google Static Hosting Guide](https://cloud.google.com/storage/docs/hosting-static-website)
[Cloudflare as CDN](https://cloud.google.com/storage/docs/troubleshooting#https)

<!-- TODO: following this guide to set up cloudflare: https://devopsdirective.com/posts/2020/10/gcs-cloudflare-hosting/#cloudflare
<!-- this blog (from comment of devopsdirective article) was also helpful for setting up cloudflare: https://dublog.net/blog/cloudflare-static-site/ -->
<!-- TODO: this guide fixed the wwww -> apex domain redirect: https://developers.cloudflare.com/pages/how-to/www-redirect/  -->

once its done and working, make a note of it somewhere here

```
# Create bucket
gsutil mb gs://davidtom.dev

# Configure web settings for bucket
gsutil web set -m index.html -e 404.html gs://davidtom.dev

# Make objects public
gsutil defacl ch -u allUsers:R gs://davidtom.dev
gsutil iam ch allUsers:objectViewer gs://davidtom.dev
```

# Build and Deploy

```
# build site to public/ folder
hugo

# deploy
GOOGLE_APPLICATION_CREDENTIALS=<path to credentials> hugo deploy
```
