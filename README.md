# STACK Website

This repository generates the main website for the [STACK online assessment system](https://github.com/maths/moodle-qtype_stack), and makes it available on [https://www.stack-assessment.org](https://www.stack-assessment.org). Additions and modifications are welcomed.

#### What is covered in this document

* The framework of the main STACK website
* Updating the website
* Testing the website locally

#### What is not covered in this document

Documentation for the STACK system is held in the docs website [docs.stack-assessment.org](https://docs.stack-assessment.org). The online STACK docs are generated directly from the [main STACK repo](https://github.com/maths/moodle-qtype_stack), so that is also where you will find the [STACK online Docs instructions](https://github.com/maths/moodle-qtype_stack/blob/master/doc/en/Developer/Website.md).

An introduction to git and markdown are given in a more detailed guide to [updating this website](WebsiteDocs/WebsiteUpdates/).

## Website framework

The website is built using [MkDocs](https://www.mkdocs.org/), a static site generator. The site pages are written in a mixture of Markdown and html within the `website_files` directory. When the site is deployed, MkDocs will convert these files into HTML and push them to the `gh-pages` branch.

The website structure mirrors the file structure: the file `website_files/Legal/Accessibility.md` will be available on `www.stack-assessment.org/Legal/Accessibility`. Every sub-folder has an `index.md` file that will take that folder's name on the website: `website_files/CaseStudies/index.md` will be available on `www.stack-assessment.org/CaseStudies/`.

MkDocs is configured in the `mkdocs.yml` file. MkDocs has a full list of [available configuration options](https://www.mkdocs.org/user-guide/configuration/). MkDocs can either generate the navigation bar automatically, or accept a custom navigation configuration in the `nav` variable. The main STACK website uses the second option. When new pages are added, they must be manually specified under the `nav` variable. Any files that are not specified in `nav` will be "hidden", that is, they cannot be accessed from the navigation bar, only from a direct link.

MkDocs cannot display MathJax out-of-the-box, so we use the markdown extension [mdx_math](https://github.com/mitya57/python-markdown-math), specified in `mkdocs.yml`, with the variable `extra_javascript` set to include MathJax.

MkDocs can accept a third-party theme, and the main STACK website uses the [Bootstrap Theme](https://github.com/mkdocs/mkdocs-bootstrap), which uses all the website building tools of [Bootstrap](https://getbootstrap.com/docs/4.0/getting-started/introduction/). This includes Bootstraps [responsive grid system](https://getbootstrap.com/docs/4.0/layout/grid/) and its [card styling](https://getbootstrap.com/docs/4.0/components/card/). Parts of the theme can be overridden in the `overrides` folder. The `main.html` file is set up to extend the base Bootstrap theme, to for example, add a custom footer. A custom stylesheet is also added, under `website_files/custom.css`.

The site is hosted by [GitHub Pages](https://pages.github.com/) from the `gh-pages` branch. A workflow under `.github` ensures that MkDocs runs its command `mkdocs gh-deploy` every time the repository is pushed to, which rebuilds the website and pushes the built HTML piles to the `gh-pages` branch. This overrides all the files currently in the `gh-pages` branch, so **you must never edit files directly in the `gh-pages` branch**.

## Updating the website

You can make small changes directly and push the changes. You do not need to download MkDocs or any of the extensions to update the website. For more substantial changes, if you are new to this you can use [this guide](/website_files/WebsiteDocs/WebsiteUpdates.md) on how to update the website.

### Adding a page

Only pages in the `website_files` directory will be included. You can write your page in markdown, and include html code. To include your page in the main navigation, remember to specify it in `mkdocs.yml`.

### Linking

Links between pages are relative. If a link starts with `/` it will be taken relative to the root of the website, i.e. `/CaseStudies/` always link to `stack-assessment.org/CaseStudies/`, while `CaseStudies/` is a relative link that appends `CaseStudies/` to the end of the current url. Absolute links to other websites must start with `https://`

### Accessibility

When adding to the STACK website, please consider all users. Some may be accessing the information you are wishing to comunicate, in a way you may not have considered. This can be physically different formats such as mobile phones and tablets, use of accessibility tools such as screen readers and keyboard controls or simply a different perspective such as colourblindness or dyslexia.

Please consider/check the following key points when making changes:

 -  Different screen sizes and zoom levels: elements should be responsive to changes in size. 
    - Use divs instead of tables as much as possible.
    - Make use of Bootstrap's responsive grid system detailed in the [bootstrap documentation](https://getbootstrap.com/docs/4.0/layout/grid/).

 - Images: Add **meaningful** alternative text to all non-text objects in particular images. This can be done using `<img src="/path/to.img.jpg" alt="Alt text">` in HTML, or `![Alt text](/path/to/img.jpg)` in markdown. It is important that this text conveys the information that the 
picture would have if viewed. If there is text in the image then this 
must be given. Do not paraphrase this text. If the text is the only information you wish to communicate, consider if you could type it out using html environments, e.g. code snippets and mathematical equations. Some useful
guidance on alternative text is given by [Harvard Univeristy](https://accessibility.huit.harvard.edu/describe-content-images).

- Links: Please add text to links rather than a full `hhtps://` link, as it slows down screen reader users and makes navigation using verbal comands very difficult. However, avoid link text such as 'here' or 'read more', make each link disernable from other links on the page, and make it as clear as you can where the link leads just from the text. Some useful guidance on hyperlinks is given by [Yale University](https://usability.yale.edu/web-accessibility/articles/links).
  
- Colour: do not use colour alone to convay meaning e.g. in a plot. Ensure your text has contrast levels of at least 4:5:1, this can be easily checked with the [WebAIM contrast checker](https://webaim.org/resources/contrastchecker/). 

 Detailed guidance on digital accessiblity are given by the [WCAG 2.1 Accessibility Guidelines](https://www.w3.org/TR/WCAG21/). 
 


Some work has already been done to make the website automatically be accessible. In particular, tables will collapse when the screen is small.

We keep track of the current state of Accessibility in our [Accessibility document](/website_files/Legal/Accessibility.md), which is available on the website to all users. Please ensure "Steps taken" is always up to date. You are invited to fix some of the "Known issues".

## Testing the website locally

Before adding major changes to the website, you are encouraged to test your changes locally. For this, you will need to install MkDocs and all the required extensions.

1. [Install MkDocs](https://www.mkdocs.org/), including its requirements.
2. Install Bootstrap with `pip install mkdocs-bootstrap`
3. Install the markdown extension with `pip install https://github.com/mitya57/python-markdown-math/archive/master.zip`
4. Install the include_dir_to_nav plugin with `pip install mkdocs-include-dir-to-nav`

You can run a local version of the website with the command `mkdocs serve`. This will make your local version available on the IP `http://127.0.0.1:8000/`.

Please test your changes work on:

- The following browsers: Chrome, Firefox, Safari, Edge.
- The following sizes: Computer, tablet, mobile. Chrome's "inspect" tool works well for this.

