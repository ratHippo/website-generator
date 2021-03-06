# Spiider

## About:
Spiider is a python script for generating websites (Spiider makes webs). It takes a markdown file and converts it to html using a template and metadata from either the markdown itself or an external json file. It also copies over any other files, meaning you can add plain HTML or assets. It then uses templates for an index page and templates for previews to generate an index page. It does the same thing as the index page for rss using different templates.

## Configuration
The sample configuration file "config.py" defines a sample config. You can get this config in any way you want, all that matters is that you have a list of subconfigs named "folders".

|   Property  |   Details   |
|-------------|-------------|
| srcdir | The directory with the source articles |
| indexdir | The directory in which to place the index page |
| indexlinkdir | the link from the indexdir to the builddir |
| builddir | The directory in which to place the built articles |
| articletemplate | The template HTML for an article Use {title} and {text} to place the title and text |
| indextemplate | The template HTML for the index page. Use {previews} to place the article previews |
| previewtemplate | The template HTML for the article previews seen on the index page. Use {indexlinkdir} for the indexlinkdir (see above). Use {path} for the path of the article (if you use {indexlinkdir}+{path} then you get the link to the article). You can use {title}, {description}, and {date} for the title, description, and date.|
| dorss | Whether or not to generate an RSS feed. True or False |
| rsstemplate | RSS template, use {items to put in the rss items}|
| rssitemtemplate | use {title}, {path}, and {description} to get the title, path and description |

## Writing
To write an article, first make a folder with the name of the article in the source directory. Then create a markdown file named "article.md" in that folder. Any files placed in the folder with the "article.md" file, excluding the name "metadata.json" will be copied into the build. This means you can place any assets you want here. To create metadata for your article you have two options:
* Markdown metadata (recommended, uses yaml format)
* json metadata (Create a seperate file called metadata.json)

For markdown metadata use the article.md file. the metadata should be at the top of your article and look like this:
```
---
title:{insert title}
description: {insert description}
date: {insert date}
path: {insert path}
testing: {insert testing (bool)}
---
```
See the table below for what each point of data means
| Property | Details |
|-|-|
| title | The title of the article |
| description | A short description of the article |
| date | The date the article was written |
| path | The name of the folder that you created for the article
| testing | True or false: if false the article will be ignored by the builder|

## Dependencies

```bash
pip3 install json markdown markdown-full-yaml-metadata
```