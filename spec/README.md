# How to build TTML2

To build TTML2 spec, you need to have Apache ant installed.

## Using Mercurial

__TODO:__ fix this when we know how to build without Mercurial's keywordmaps feature to put dates and times in.
Make sure the following are included in your .hgrc as well as whatever else you need to make hg go, like your username in [ui], w3c authentication in [auth], proxy in [http_proxy] if you need it, etc:

--
[extensions]
keyword =

[keyword]
ttml2/spec/ttml2.xml =

[keywordmaps]
Author = {author|user}
Date = {date|utcdate}
Header = {root}/{file},v {node|short} {date|utcdate} {author|user}
Id = {file|basename},v {node|short} {date|utcdate} {author|user}
RCSFile = {file|basename},v
RCSfile = {file|basename},v
Revision = {node|short}
Source = {root}/{file},v
--

To edit and build, if you are the Editor:

1. hg pull -u
2. edit ttml2.xml
3. ant sg
4. if more edits, goto 2
5. hg revert -C ttml2.html
6. hg commit -m [your commit message here]
7. ant rgc
8. hg push

Line 5 reverts the html, line 6 commits just the changes you made to the source xml, line 7 regenerates the ED and commits it with a standard message, and line 8 pushes the changes including the html back to the repository.

If you're Not the Editor but want to push a change, omit steps 7 and 8 and replace with:

9. Email the Editor notifying of the changes so that the Editor can review your change and push the regenerated ED.

--
When committing, you can enter multi-line commit messages more easily by omitting the -m argument; you can then edit your message in your standard editor (e.g. vi).

Commit messages should have at least a first line be preceded by [ttml] with a summary of the changes. Subsequent lines can be used for further detail.
