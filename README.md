# David Tomczyk's Personal Site

<!-- TODO: review theme features: https://themes.gohugo.io/themes/hugo-sustain/#features -->
<!-- TODO: set up favicon and other site metadata -->

# Development

```
hugo server
```

# Production

See Hugo Deploy instructions for GCS [here](https://gohugo.io/hosting-and-deployment/hugo-deploy/)

## Bucket Set Up

[Bucket settings source](https://qualityandinnovation.com/2020/12/23/pushing-your-hugo-site-to-a-gcs-bucket-part-3/)
[Domain configuration source](https://gist.github.com/p10rahulm/5d23f58ceca389a99594dde52849b381)

<!-- TODO: left off with domain configuration - getting an SSL erro
maybe I need to follow google's guide instead? https://cloud.google.com/storage/docs/hosting-static-website
(linked in bottom comment of github gist)
TODO: maybe I need to set up cloudflare as a CDN? https://cloud.google.com/storage/docs/troubleshooting#https
 -->

```
# Create bucket
gsutil mb gs://www.davidtom.dev

# Configure web settings for bucket
gsutil web set -m index.html -e 404.html gs://www.davidtom.dev

# Make objects public
gsutil defacl ch -u allUsers:R gs://www.davidtom.dev
gsutil iam ch allUsers:objectViewer gs://www.davidtom.dev
```

# Build and Deploy

```
# build site to public/ folder
hugo

# deploy
hugo deploy
```
