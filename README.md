isecpartners.github.io
======================

This is our externally-facing research page. Use this site to describe tools,
add blog posts, reference whitepapers or presentations, etc. If you'd like to
make a change, please fork this repository and submit a pull request.


Jekyll Tutorial
---------------

Installing Jekyll:

    gem install jekyll


Previewing the site locally at http://localhost:4000 :

    jekyll serve -w


Creating a new blog post
------------------------

__You do not need to have Jekyll installed__ in order to create a new blog post.
However, you will not be able to preview how the post will look on the blog using
Jekyll's serve command.

First you need to fork this repo. Then, you can add your blog post by creating
a .markdown file within the _posts/ folder. The file name should follow this
convention: YYYY-MM-DD-name-of-the-post.markdown.

You can then write your blog post in this file using the Markdown syntax. Feel
free to look at the existing blog posts to get examples.

After writing your post, you can preview it if you have Jekyll installed:

    jekyll serve -w

Once you're ready to post your article, just submit a pull request.

Categories
----------

If you need to add another, please follow these specific guidelines:

* Don't make a category about a specific conference or project
* Do make a category about a specific technology
* Do make a category about a specific project when this is the second post about it. Add the category to your first post at this time also
* Do make the category all lowercase


Approved/Encouraged categories:

* whitepapers
* advisories - for items related to a bug we found, or advice we are giving relating to a popular bug
* tools
* ssl - yes even TLS topics
* sslyze
* passwords
* news - for items that don't fit anywhere else. E.G. announcing we are working with a particular project or the like, sponsoring a conference
* ios
* introspy
* fuzzing
* crypto
* conferences - for releasing slides, tools, or otherwise references a conference you presented at or we're sponsoring.
* android
* aws