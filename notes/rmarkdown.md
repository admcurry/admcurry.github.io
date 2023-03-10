[<kbd> <br>  Home  <br> </kbd>](https://atcurry.github.io)
[<kbd> <br>  About  <br> </kbd>](https://atcurry.github.io/about.html)
[<kbd> <br>  Notes  <br> </kbd>](https://atcurry.github.io/notes.html)
[<kbd> <br>  Coding  <br> </kbd>](https://atcurry.github.io/coding.html)
[<kbd> <br>  Data Analysis <br> </kbd>](https://atcurry.github.io/data.html)
[<kbd> <br>  Projects (r)  <br> </kbd>](https://atcurry.github.io/rprojects.html)
[<kbd> <br>  Projects (julia)  <br> </kbd>](https://atcurry.github.io/juliaprojects.html)
[<kbd> <br>  Projects (python)  <br> </kbd>](https://atcurry.github.io)
[<kbd> <br>  Repo's  <br> </kbd>](https://atcurry.github.io/repos.html)

---

<div align="center"> <h1> R Markdown Cheatsheet </h1> </div> <br/>

### Introduction to R Markdown
An R Markdown document is made of three components: the code, the text of the report, and the metadata for the file.
    
When finished modifying a file and ready to see the report, we'll need to knit it. Knitting a file is how we generate an output file from the R markdown file. When a file is knit, R Markdown runs the chunks of R code contained in the file and combines them with the text in the document into an HTML file.

Code chunks, headers, formatting text, inserting links and images are done similarly to markdown.

---

### The YAML Header
The YAML header containing the metadata appears at the top of the file, followed by the contents that make up the report, including the text and code in code chunks. YAML is a syntax for hierarchical data structures that is commonly used for configuration files.
```
---
title: "Investment Report"
author: "Adam"
date: "`r format(Sys.time(), '%d %B, %y')`"
output: html_document
---
```

---

### Customising Plots
The plot can be edited in the header of the code chunk, for example to decide the alignment, the size, and to add a caption.
```
```{r investment-annual-summary, fig.dim = c(5.3), out.width = '50%', fig.align = 'centre', fig.cap = 'Figure 1.1'}

ggplot...
```

Plots can also be customised in the r setup chunk, so the specified settings apply globally.
```
```{r setup, include = F}
knitr::opts_chunk$set(fig.align = 'centre', echo = TRUE)
```

---

### Tables
Tables can be added using the `kable()` function from the `knitr` package.
```
```{r tables}
kable(dataframe, col.names = c('name1', 'name2'), align = 'cc', caption = 'Caption')
```

---

### Code Chunk Options
**Include:**
Code runs but does not appear in the report, results do not appear.
```
```{r setup, include = FALSE}
code
```

**Echo:**
Code runs but does not appear in the report, results do appear.
```
```{r setup, echo = FALSE}
code
```

**Eval:**
Code appears in the report but does not run, results do not appear.
```
```{r setup, eval = FALSE}
code
```

---

### Warning & Error Messages
**Collapse Warnings to One Chunk:**
Rather than a warning message appearing in a separate chunk after the code output, this will make it appear in the same chunk.
```
```{r ___, collapse = TRUE}
code
```

**Turn Off Warnings:**
```
```{r ___, warning = FALSE}
code
```

**Errors:**
The report will still knit if there is errors, and will show an error message. (By default, the report will not knit if errors are present in code.)
```
```{r ___, error = TRUE}
code
```
---

### Table of Contents
```
---
title: "Investment Report"
author: "Adam"
date: "`r format(Sys.time(), '%d %B, %y')`"
output: 
	html_document:
		toc: true
		toc_float: true
		toc_depth: 3
		number_sections: true
---
```
- The `toc: true` line adds the table of contents.
- The `toc_float: true` line makes the contents appear always on the left, like a menu bar.
- Under `toc_float`, `collapsed: false` and `smooth_scroll: false` can be added.
- The `toc_depth` line specifies how many layers deep the table of contents shows.
- The `number_sections` line specifies whether or not to number sections in the report.

---

### Parameters
Parameters can be added to the YAML header, in this example the parameter country has been added, and Brazil has been specified in this case.
```
---
title: "Investment Report"
author: "Adam"
date: "`r format(Sys.time(), '%d %B, %y')`"
output: html_document
params:
	country: Brazil
---
```
In the code, instead of ‘Brazil’, use params$country.

---

### Styles
To reference a CSS file, add the following to the YAML header.
```
---
title: "Investment Report"
author: "Adam"
date: "`r format(Sys.time(), '%d %B, %y')`"
output:
	html_document:
	css: styles.css
---
```