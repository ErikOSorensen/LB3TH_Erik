# LB3TH_Erik website: The new lb3th.no

In this directory, I want to create a website to be written in Quarto (with
computational R and Python parts) and eventually replace https://lb3th.no/. The
website will document my experiments in RF and electronics, and maybe once in a
while also radio experiences. This will continue the now abandoned lb3th.no
pages.

Publication will be through pushing to github, and then attempt to have 
netlify work to publish the pages. This is how the current lb3th.no site is 
configured to work, but the tooling for that is getting old. 

## The structure of the new site

There will be two main types of pages published. Lab notes, that are published
chronologically (based og date in the Quarto code, not on actual date they
are written), and project sites that are related to the lab notes, but will
only create a list of the lab notes at the bottom. In one way or another, I want
the lab notes to be able to specify projects (maybe with category tags), such
that when a project page is written it can specify tags/categories of lab notes
to create a list of at the bottom of the page. I don't want the name "project"
to be visible to readers, since one such page might be about the

I also want an "about" page and a "contact" page. 

Earlier, I used Rstudio to write my pages. I now want to transition to 
Positron. 

## The look of the new site

I want a modern look, using Roboto or some such font for main text and Google
Sans Code for any code to be shown. If you find these to fit badly together, I
am happy for other suggestions. 

## Transitioning old to new site

When the new site appears nice in a local setting, I want to shut down
the current lb3th, and have the new site published to the lb3th.no domain
(which I own). I will then publish even if the new site hasn't got a lot 
of content yet. 

When the new site code and publication scheme is in place to publish for the new
site, I will manually transition the posts from the old site into the new. 

## Documentation

I would like for you to write an readme.md file that explains how to use it (add
pages, including photos and graphs calculated by R or Python, having the
project/tags work). I am also used to writing new "uv" specification in each
directory, and maybe I can do so for the Quarto pages? Please let me know. 
