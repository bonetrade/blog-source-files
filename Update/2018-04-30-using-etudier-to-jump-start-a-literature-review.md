+++
title= "Using Etudier to Jump Start a Literature Review"
date= 2018-04-30T11:30:45-04:00
description = "A workflow for starting that literature review"
draft= false
+++

2018-04-30

### The Literature Review

How do you start a literature review on a new project? We're not starting from scratch, of course - we've got the pages of bibliography that we generated when we first starting scratching out what this project could be about. We started *that* step by considering the bibliography we had to hand as we wrote our first paper. Nothing is ever *truly* from scratch, in academia.

But we can certainly jump start the process. One way we can do that is by pulling from one of the largest bibliographic databases readily to hand - Google Scholar. G-Scholar was built by ingesting several existing databases and is maintained by whatever magic Google uses to index journal websites and so on. We can search this database not only how we might search with the regular Google search page, but also via the citation graph. We can give it a reference, and search not only what *that* paper cites, but also the papers that cited it in turn. What's more, we can automate this process.

![Etudier](https://raw.githubusercontent.com/edsu/etudier/master/example/output.png)

Ed Summers has created a python package called '[Etudier](https://github.com/edsu/etudier)' which handles this for us. It mimics a user paging through search results. By default it only looks at the first ten citations for a page or a search result, and then the top 10 for each of those, thus 100 results. That might be enough to get going. But by fiddling with the `--pages` and `--depth` flags, you can collect much much more. `pages` will search through x number of pages of results, while `depth` will delve that far into each result's citations.

I ran the following:
```
$etudier.py 'https://scholar.google.com/scholar?hl=en&as_sdt=0%2C21&q="instagram"&btnG=' --pages 2 --depth 2
```

...to see what the broader landscape of scholarship around Instagram looked like. This produced 1.4 mb of results, or 1883 articles tied by 2179 edges. 

As a graph, we spot something interesting right away:

![A citation graph](/update/2018-04-30-using-etudier-to-jump-start-a-literature-review_files/etudier1.png)

Two broad clumps, or two extremely distinct ways of referring to 'Instagram'. We can then explore subclumping by searching for communities or patterns of link similarities (aka as 'modularity'):

![Modularity within the citation graph](/update/2018-04-30-using-etudier-to-jump-start-a-literature-review_files/etudier2.png)

Often however this kind of visualization is not of much use, other than how we've already used it. Instead, let's look for centrality in this graph, and identify those works whose pattern of linkages enable them to bridge these various subgroups. I presume that such works have something about them that speaks to these different aspects of scholarship and so are the works that I'll want to start with for my review. Using [gephi](http://gephi.org) I calculate eigenvector centrality (roughly, the centrality that comes from being wellconnected wellconnected others).

![centralities in the graph](/update/2018-04-30-using-etudier-to-jump-start-a-literature-review_files/etudier3.png)

You can download our graph of data for yourself [here](/Update/instagram-d2-p2-output-table-apr30-2018.csv).