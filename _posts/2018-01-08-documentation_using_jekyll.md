---
title: "Documentation using Jekyll"
sidebar: home_sidebar
permalink: documentation_using_jekyll.html
summary: "Avalon Media System's documentation is moving to a Jekyll-powered site."
---

## Work in Progress

Please be patient as we work to migrate our technical documentation over to this site. The migration will also serve as a chance for us to rework some of the documentation and weed out unnecessary or outdated material. In the meantime, continue to reference our [documentation wiki](https://wiki.dlib.indiana.edu/display/VarVideo/Avalon+Media+System) as needed.

## Why Jekyll?

All of Avalon's external public documentation will henceforth be managed on a site built with [Jekyll](https://jekyllrb.com/)--a static site generator--and a [documentation theme](http://idratherbewriting.com/documentation-theme-jekyll/mydoc_about.html) created by Tom Johnson. Jekyll allows for microscopic levels of customization while simultaneously supporting an efficient workflow for pre-formatted content. In particular, the move to Jekyll is attractive for two primary functions:

### GitHub Integration

Because Jekyll powers GitHub Pages, it can be used to easily generate a site from code held on GitHub. Since the code for Avalon is also held on GitHub, this means that the documentation will be held in the same location as the project code, and be managed in the same way. Our developers will be able to contribute to the documentation easily, using nothing more than simple markdown, and the documentation will be subject to a familiar workflow.

### Division of Products

Our previous method for handling documentation--Confluence--worked well for collaborative editing, but was difficult to adapt to the release schedule of the Avalon Media System. Avalon has both minor and major releases, with new features being added all the time. However, not all Avalon adopters are using the most current version of the software. Therefore, documentation is tied closely to a specific version, and while Confluence managed the version history of every document, finding the correct document for a specific version of Avalon was non-intuitive.

Tom Johnson's documentation theme helps to counter this problem. The theme divides documentation by product, generating a new navigational sidebar displaying only the relevant information for that product. Products map onto major versions of Avalon in our instance: each version of Avalon will display only the relevant documentation. When a new version of Avalon is released, the directory containing the previous documentation will be frozen and cloned. The cloned directory will be updated to reflect the latest release and become the active documentation. The ensures that an entire set of documenation will be maintained for each version of the software.

{% include links.html %}
