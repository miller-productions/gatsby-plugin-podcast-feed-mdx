# gatsby-plugin-podcast-feed-mdx

This [Gatsby plugin](https://www.gatsbyjs.org/docs/plugins/) will generate a podcast rss feed that is published on your site.

It can be used to submit to podcast directories such as [Apple Podcasts](https://help.apple.com/itc/podcasts_connect/), [Stitcher](https://partners.stitcher.com/join), [Spotify](https://podcasters.spotify.com/), [Google Podcasts](https://developers.google.com/search/docs/guides/podcast-overview), [TuneIn Radio](https://tunein.com/podcasts/), [Pandora](https://www.ampplaybook.com/podcasts), [Listen Notes](https://www.listennotes.com/submit/), [iHeartRadio](https://www.iheart.com/content/submit-your-podcast/), [AnyPod](https://anypod.net/publish) etc...

The section in the feed that describes the podcast itself is based on values configured in your `gatsby-config` file.

Descriptions for each episode are generated based on values configured within individual mdx files, i.e. one for each episode.

The feed will be written out to a site root-relative path specified in `gatsby-config`.

## Pre-requisites

This plugin assumes the following:

1. You are using [gatsby-plugin-mdx](https://www.gatsbyjs.org/packages/gatsby-plugin-mdx/) in your site to generate pages from markdown files.
2. You will have one markdown file per podcast episode.

See here for background:

* https://www.gatsbyjs.org/docs/mdx/
* https://mdxjs.com/getting-started/gatsby

## Installation

```sh
npm install --save gatsby-plugin-podcast-feed-mdx
```
or
```sh
yarn add gatsby-plugin-podcast-feed-mdx
```
## Usage

### Your gatsby-config.js File

```js
// In your `gatsby-config.js`
module.exports = {
  plugins: [
    {
      resolve: `gatsby-plugin-podcast-feed-mdx`,
      options: {
        title: `Podcast Title`,
        subtitle: `A pithy tagline`,
        description: `Podcast description`,
        summary: `Podcast summary`,
        podcastType: `episodic`,
        siteUrl: `https://podcast.com`,
        imageUrl: `https://podcast.com/podcast-image/png`,
        feedUrl: `https://podcast.com/pocast-rss-feed.xml`,
        language: `en-au`,
        copyright: `Copyright © 2020 Some Owner`,
        authorName: `The Author`,
        ownerName: `The Owner`,
        ownerEmail: `owner@podcast.com`,
        managingEditor: `editor@podcast.com`,
        webMaster: `support@podcast.com`,
        explicit: `no`,
        publicationDate: `Jan 25, 2020 10:00:00 GMT`,
        category1: `Arts`,
        subCategory1: `Books`,
        category2: `Education`,
        subCategory2: `Courses`,
        category3: `Business`,
        subCategory3: `Marketing`,
        timeToLive: `60`,
        outputPath: `/podcast-rss-feed.xml`
      },
    },
  ],
}
```

### Your Podcast Episode Mdx File(s)

```text
// In each `.mdx` file you have (one per episode)
---
type: podcast-episode
slug: /your-website-path/to-this-episode
title: Hello, podcast!
subtitle: The first ever episode.
publicationDate: 2019-01-29
author: Podcast host
season: 1
episodeNumber: 1
episodeType: trailer
excerpt: Here is the excerpt for the first podcast episode.
url: https://podcast.com/podcast/episode.mp3
size: 206820339
duration: 3414
explicit: false
categories:
  - Category 1
  - Category 2
---

Your main content here.

Why hello there, I'm a podcast episode!

```

## Output

The main output of this plugin is an rss file for a podcast.

The structure of the generated rss file has been designed to support [Apple Podcasts requirements](https://help.apple.com/itc/podcasts_connect/#/itcb54353390) and [Google Feed requirements](https://developers.google.com/search/reference/podcast/rss-feed)

The rss file is generated when you run `gatsby build`. (*note: the rss file is **not** generated when you run* `gatsby develop`)




## Related Info
For information about the general rss feed specification, see the following:
* [Official RSS Spec](http://www.rssboard.org/rss-specification)

For information about podcast-specific rss feed specifications, see the following:
* [Apple Podcasts Connect Help](https://help.apple.com/itc/podcasts_connect/#/itcb54353390)
* [Google Feed Requirements](https://developers.google.com/search/reference/podcast/rss-feed)
* [Spotify Podcast Delivery Specification](https://podcasters.spotify.com/terms/Spotify_Podcast_Delivery_Specification_v1.6.pdf)
* [Ryan Parman's iTunes Podcast RSS Spec](https://github.com/simplepie/simplepie-ng/wiki/Spec:-iTunes-Podcast-RSS)
* [FeedForAll iTunes Tags Tutorial](https://www.feedforall.com/itune-tutorial-tags.htm)
