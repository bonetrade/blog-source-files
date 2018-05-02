+++
title = "Building a Website with Blogdown"
description = "A short tutorial on using blogdown to build a website"
weight = 110
+++

This website is built with blogdown. 

```
setwd("/Users/path/to/your/files/username.github.io")
blogdown::new_site(dir = "usernameFiles", #New Directory within working directory where web content will be stored
                   theme = 'vjeantet/hugo-theme-docdock', #theme information
                   format = 'toml') #specify toml instead of yaml

setwd("usernameFiles")
blogdown::build_site()
blogdown::serve_site()
```

That builds the shell of the site in a subfolder inside your username.github.io repository on your computer. 

`blogdown::build_site()` builds your website. Copy the contents of the generated public folder to the username.github.io directory. 

```
git add .
git commit -m "first commit"
git push -u origin master
```

The insert image add-in for blogdown makes putting your image in the correct spot a whole lot easier. Make sure to install it. For the full rundown on how to use blogdown, see [the manual](https://bookdown.org/yihui/blogdown/).
et voila.

With this particular theme, you generate the navigation structure by nesting folders inside folders and each subfolder has its own `_index.md` file. In that index file you have `weight = 10` or whatever value in the TOML so that folders at the same level of the hierarchy appear in the correct order.

In your terminal, navigate to your usernameFiles folder, and run `hugo server`. Then, any changes you make in rStudio to your source files is automatically reflected at `localhost:1313` in your browser.


