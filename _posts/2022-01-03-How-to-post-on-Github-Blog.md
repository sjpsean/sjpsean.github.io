---
layout: single
title:  "How to post on Github Blog"
categories: 
    - Github Blog
tags: 
    - [git, TIL, blog, github, jekyll, github pages]
---

### How posting works in Jekyll

Every posts in Jekyll have to be saved in your _posts directory with the format:  
`YEAR-MONTH-DAY-title.md`  YEAR (four digits), MONTH and DAY (two digits).  
For example, `"2022-01-03-how-to-post-jekyll.md"` will be your post’s filename.  
You can check this information from [Jekyll website](https://jekyllrb.com/docs/posts/)

- **Go to your [github.io](http://github.io) repository and click on “Add file” and “Create new file”.**
- **Write `_post/2022-01-03-title.md` (year, month, day and title can be replaced) for the name of the file.**

Another important thing is a [Front Matter](https://jekyllrb.com/docs/front-matter/)
According to the website, "Any file that contains a [YAML]([https://yaml.org/](https://yaml.org/)) front matter block will be processed by Jekyll as a special file."

For example, this YAML code is written at the very beginning of this post.

```yaml
---
layout: single
title:  "How to Post on Github Blog"
categories: Github-Blog
tags: git TIL blog github jekyll githubpages
---

# You can follow this form if you want to use two words or more as a name of your category or tags. 
---
layout: single
title:  "Data Structures - What is it?"
categories: 
    - Data Structures
tags: 
    - [TIL, Big-O, Algorithms, Data Structures]
```

More things can be written between those two `---` lines. You can read more about what you can set up for your post using Front Matter [here](https://jekyllrb.com/docs/front-matter/)

- **Now, add the Front Matter at the beginning of your post.**
- **Write whatever you would like after the Front Matter and Click “Commit new file” at the bottom of the page.**  


You just posted your first post on your blog! To check if it is working, go to `[https://your_username.github.io](https://your_username.github.io)` (it might take a few seconds to be updated).