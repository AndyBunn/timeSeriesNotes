--- 
title: "A collection of note for ESCI 504"
author: "Andy Bunn"
date: "08-August-2025"
description: "Helpful materials for ESCI 504"
#github-repo: make one OpenDendro/dplR-workshop
documentclass: book
bibliography: [packages.bib,otherRefs.bib]
#csl: global-change-biology.csl
biblio-style: apalike
link-citations: yes
site: bookdown::bookdown_site
output: 
  bookdown::gitbook:
    includes:
      in_header: hide_code.html # inspired by: https://stackoverflow.com/questions/45360998/code-folding-in-bookdown
    config:
      toc:
        collapse: section
        scroll_highlight: true
        before: null
        after: null
    split_bib: no
---

# Preamble

This document is a compilation of notes, examples, and exercises developed for our course on time series analysis, with a particular focus on environmental applications. Rather than follow a traditional textbook, we’ve taken a modular, hands-on approach. Each section builds on what came before, emphasizing interpretation, practical tools, and critical thinking about how time series models apply to real-world environmental questions.

You’ll find annotated code, worked examples, and commentary throughout — some informal, some technical — all aimed at helping you *do* time series work, not just read about it. The examples often draw from environmental data: climate records, ecological time series, and other systems that change over time and space. But the core ideas and tools are broadly applicable.

From time to time, I’ll refer you to more formal textbooks or peer-reviewed articles to go deeper into theory, context, or application. These serve as complements, not replacements, for what we’re doing here.

The tone of these notes is meant to be accessible, pragmatic, and occasionally opinionated. You’ll see suggestions, cautions, and nudges — all based on what I’ve found helpful (and confusing) when learning and teaching these methods.

This isn’t a comprehensive or final text. It’s a live document, shaped by your questions, feedback, and curiosity. Think of it as a field guide: not everything you’ll ever need, but hopefully exactly what you need to get your bearings, spot the patterns, and know what to do next.

**Please note! This is a very drafty document and there are typos and all kinds of silliness in it.**

## Technical Setup

This document was written in Markdown using the **bookdown** package and built with **R version 4.5.0`**. You should be up to date — or at least close — on your versions of R, RStudio, and relevant packages. You can keep your packages updated by running:

```r
update.packages()
```

### Project Structure

To follow along with the examples, you’ll need a working RStudio project. Here’s what to do:

1. **Create a new RStudio project**  
   Go to **File → New Project → New Directory → New Project**. Give it a name (e.g., `timeseries-notes`) and choose where to save it.

2. **Download the `data/` folder**  
   You’ll find a folder named `data` that contains most of the datasets we’ll use (anything we don’t download directly in the code). Save this folder inside your project directory.

   Your folder structure should look like this:
   ```
   timeseries-course/
   ├── data/
   │   ├── HansenSockeye.rds
   │   ├── jul65N.rds
   │   └── ...
   └── timeseries-notes.Rproj
   ```

3. **Refer to data files using relative paths**  
   In your code, use paths like `"data/jul65N.rds"` rather than full file paths. This makes your work portable and easier to share or rerun later.

4. **Store your own scripts in the root directory**

Any code you write for homework, labs, or your own exploration should be saved in the main project folder (alongside the .Rproj file). This keeps your work organized and ensures it runs smoothly within the project environment.


If you’re new to R projects, the key idea is this: treat your project folder as your workspace. All code, data, and outputs should live inside it. It makes everything cleaner and reproducible.


### Why Use Projects in R?

Think of an RStudio project like a **toolbox** or **field kit**. Everything you need for an analysis — your scripts, data, figures, notes — lives in one container. When you open the project, RStudio knows: *this is your workspace*. You don’t have to tell it where to find files or worry about breaking things if you move the folder.

Projects help you:

- Keep everything for a project in one place  
- Use **relative paths** (like `"data/file.csv"`) that work on any computer  
- Avoid hard-coded `setwd()` calls that break when folders change  
- Switch between different projects without mixing things up  
- Work seamlessly with Git and other tools for version control  

In short, RStudio projects make your work more organized, more robust, and easier to share.

### Why Reproducibility Matters

Science is only as strong as its ability to be checked, tested, and built upon. Reproducibility means that **someone else — or your future self — can rerun your analysis and get the same results**.

In the world of data analysis, that means:

- Your code runs start to finish without manual tweaking  
- Your data is accessible, documented, and versioned  
- Your results (figures, summaries, statistics) are generated from your code, not copy-pasted  
- You (and others) can trace how a result came to be — and rerun it with new data if needed

Working reproducibly isn't just good practice — it’s essential for credible, transparent science. RStudio projects, scripted workflows, and literate programming tools like R Markdown and Bookdown are all part of that ecosystem. This course will help you build those habits as you learn the methods.



