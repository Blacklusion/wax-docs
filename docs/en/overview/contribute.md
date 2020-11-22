# How to contribute to the Wax Docs
Currently all information regarding the WAX Blockchain is **scattered** across the different guild websites.
This documenation is an attempt in centralizing all the content that already has been published and all the future articles that will be published.
Therefore, contributing to the documentation would be very welcomed and can be easily done via GitHub.

> This documentation also has multilanguage support: A contribution can also be done in form of translating an existing article.

# Best Practices: <!-- {docsify-ignore} -->
## Folder structure
All the articles are stored in the **docs/** folder of the repository. This folder contains all parent folders of the different languages the documentation is currently available in. Select your desired **language** or create a new folder if needed.

Then, select the **category** of your article or create a new one if needed. Lastly, just store your article with "-" instead of spaces. The urls will be created based on the filename, therefore it should be consistent across all articles.

In case you are using **images** in your article: In every category folder you will find a **media/** folder. In that folder create a new subfolder with the exact name of your article. Within that folder, you can use whatever namingscheme you want.
```
.
└── docs/
    ├── index.md
    └── language (e.g. en)/
        ├── _sidebar.md
        └── Category (e.g. getting started)/
            ├── your-article.md
            └── media/
                 └── your-article/
                      ├── img01.png
                      └── img02.png
```


## Using Headers correctly
The sidebar will automatically show the table of contents of your article. It will be created based on your H1 and H2 headers. So, when you are writing your article, keep in mind to highlight important sections with at least a H2 header, so the user can directly jump to that section. Please **avoid** using ":" after your header, because it does not look as neat in the sidebar.

In case you don't want, that one of your headers shows in the sidebar, you can tell the docs engine to ignore it with the following line:

```markdown
# Getting Started

## Header <!-- {docsify-ignore} -->

This header won't appear in the sidebar table of contents.
```

If all the headers should be ignored, you can use the following line:

```markdown
# Getting Started <!-- {docsify-ignore-all} -->

## Header

This header won't appear in the sidebar table of contents.
```

## Sidebar
As mentioned before, the table of contents will be automatically created for the sidebar. But first you will have to add your article to the sidebar. In every language folder you will find a **_sidebar.md** file:
```
.
└── docs/
    ├── index.md
    └── language (e.g. en)/
        └── _sidebar.md
```
Open the appropriate file and add your article after the following scheme:
```markdown
<!-- docs/_sidebar.md -->

- Overview
  - [Contributing to the Docs](contribute.md "How to contribute to the WAX Docs")

- Getting started
  - [chains.json](en/getting-started/chains-json.md "How to create a chains.json")
  - [bp.json](en/getting-started/bp-json.md "How to create a bp.json for WAX")
  - [Pushing bp.json on chain](en/getting-started/pushing-bp-json-onchain.md "How to push your bp.json on-chain")
```
You can specify an title after the name of the markdown file. This title will not be shown anywhere on the doc site itself. This title is used for SEO purposes only and lets you to specify how your articles will be previewed.

## Linking to other articles
When linking to other articles, it is highly recommended to use relative links, since this would allow to e.g. easily change the domain name in the future. You can link to other articles by using the following format:
```markdown
This is a [link](/en/getting-started/other-article) to another article.
```
> Please link to as many other articles as possible.

## Correctly using Code Blocks
Markdown offers the option to specify the language of code blocks. The documentation supports syntax highlighting and will automatically highlight your codeblock, based on the language you specified at the beginning of the codeblock. To specify a language use the following format:

<pre>
```javascript
/**
 * Your code here
 */
```
</pre>

## Always add "Helpful Links"
Please always add a Helpful Links section at the end of your article. Thats "Helpful Links" without ":" and with capital letters at the beginning of both words. This is a standard I would like to establish: The idea is, that people can quickly find other articles regarding similar topics, links to repositories or websites that may help by solving the problem discussed in the article. Feel free to link to your own products.


## Helpful Links
- [Markdown Cheetsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
