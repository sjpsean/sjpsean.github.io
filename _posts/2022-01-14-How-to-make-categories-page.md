---
layout: single
title:  "How to make Categories page"
categories: 
    - Github Blog
tags: 
    - [git, TIL, blog, github, jekyll, github pages]
---


### Constomizing github page’s navigational links

<figure class="full">
    <a href="/assets/images/github-blog-categories.jpg"><img src="/assets/images/github-blog-categories.jpg"></a>
</figure>

  1. Go to your github pages repository and find `navigation.yml` file in `_data` folder.
  2. Add or edit titles and urls following this form (I found out the wrong spacing can cause errors).  
  ```yaml
  main:
    - title: "Categories"
      url: /categories-grid/ # These urls is a link to the pages you will set up soon.
    - title: "Tags"
      url: /tags-grid/
    - title: "Posts"
      url: /year-archive-grid/
      description: "posts for each year" # shows when hover
    - title: "Search"
      url: /search/
  ```
  3. Now, make a new folder in your repo called `_pages` and create a new file naming `category-archive.md` or `category-archive-grid.md` if you chose to have a grid view of your posts listed under the categories. (file name doesn't really matter. **permalink** is the one that you should match with the **url** in the `navigation.yml` file)
  4. In the file you create in `_pages` folder, write one of the following code to create pages of what you want.  
  
      ```yaml
      # For categories (in _pages/category-archive.md file)
      ---
      title: "Posts by Category"  # title of the 'category' page.
      layout: categories # layout can be changed to tags, posts, search, etc...
      permalink: /categories-grid/ # use this link to locate this file.
      entries_layout: grid # you can delete this line if you don't want a grid view.
      author_profile: true # set it to false if you don't want your profile shown in this page.
      ---

      # For tags (in _pages/tags-archive.md file)
      ---
      title: "Posts by Tag"
      permalink: /tags-grid/
      layout: tags
      entries_layout: grid
      author_profile: true
      ---

      # For yearly view of all posts you posted (in _pages/year-archive.md file)
      ---
      title: "Posts by Year"
      permalink: /year-archive/
      layout: posts
      author_profile: true
      ---

      # For Serach tab (in search.md file)
      ---
      title: Search
      layout: search
      permalink: /search/
      ---
      ```

  5. If you have YAML like this in your posts, you will be able to see “Github Blog” as one of your categories and number of posts you have under that cateory.  [How to post on github page](/github%20blog/How-to-post-on-Github-Blog/)  
  ```yaml
  ---
  layout: single
  title:  "How to Post on Github Blog"
  categories: 
    - Github Blog
  tags: 
    - [git, TIL, blog, github, jekyll, github pages]
  ---
  ```



[https://mmistakes.github.io/minimal-mistakes/docs/navigation/](https://mmistakes.github.io/minimal-mistakes/docs/navigation/).

