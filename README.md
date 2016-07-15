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

Post Authoring
--------------

Please abide by the following when authoring posts:

* Do not use any H1 headers (in markdown, single #). Start with the H2 header (in markdown, double ##)
* Do not separate the categories by commas

Specific tags may be added to enable certain sidebar behaviors. Note that Download, Github, and Conference all have singular versions for friendliness.

* Download
** download_name (for example 'Whitepaper' or 'ToolName Releases')
** download_link
** download_names: ["Bob", "Alice"] (for multiple links)
** download_links: ["https://www....", "https://www...."]
* Github
** github_name (name of the project)
** github_link (link to github)
** github_names (for multiple links)
** github_links
* Conferences
** conference_name (should be short and contain year  e.g. BH Arsenal '14 or BH EU '13)
** conference_link (link to your talk on the conference page)
** conference_names (for multiple links)
** conference_links
* Related
** related: ["2014/08/13/tor-browser-research-report", "2013/10/14/open-tech-fund-report-release"] (ids of specific related blog posts)
** Related links are _not_ symmetric, so if applicable you should update the earlier post also.
* CVEs
** cves: ["CVE-2016-6151", "CVE-2016-6152"]


Categories
----------

If you need to add another, please follow these specific guidelines:

* Don't make a category about a specific conference or project
* Do make a category about a specific technology
* Do make a category about a specific project when this is the second post about it. Add the category to your first post at this time also
* Do make the category all lowercase
* Do not separate the categories by commas


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

Upcoming Events/Talks
---------------------

Edit the corresponding _data/ files. While the site has logic not to show expired items, it requires the site to be rebuilt to achieve this. This can be accomplished with a dummy commit if needed; there is no need to comment or remove entries from the data files. (And please do not do so, perhaps some day we'll want to reference that data!!)  

In general, Talks is for talks at security conferences, arsenal, or a time when we're presenting something. It's totally fine (and encouraged!) to list Open Forum talks we give.

Events is for the rest. Trainings we're giving, Webinars, Open Forums, Conferences we're sponsoring. If the item doesn't have a link, but is an invite only thing, you can make the link an email link like so:  mailto:Bob.Dole@nccgroup.trust?subject=Invite%20Me%20To%20Seattle's%20Open%20Forum!!!

Items are listed in REVERSE order of the file, which means THE ITEM WITH THE DATE FARTHEST IN THE FUTURE SHOULD BE PUT AT THE TOP OF THE FILE. Each item supports the following attributes. If a value needs a colon (:) in it, enclose the entire value in quotes.

* title - Required
* subtitle - Optional. Occurs after the title, but is not linked (if a link is specified)
* link - Optional
* dates - Optional. Does not need to be formatted as a date, can be any data
* expires - Required. Must be formatted as a date
* location - Optional