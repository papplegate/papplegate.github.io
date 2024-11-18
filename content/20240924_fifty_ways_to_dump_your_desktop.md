Title: Fifty ways to dump your desktop: command-line alternatives to Microsoft Word, PowerPoint, and Excel
Date: 2024-09-24 
Category: tools

> I’d like to help you in your struggle  
> To be free  
> There must be fifty ways  
> To leave your lover...  
> Just drop off the key, Lee  
> And get yourself free  

-- Paul Simon, "50 Ways to Leave Your Lover"

With apologies to Paul, "I'd like to help you in your struggle to be free" from software tools with graphical user interfaces, especially Microsoft Word, PowerPoint, and Excel.  There are lots of ways to "get yourself free" -- I'll point out a few here.

What's wrong with Word, Excel, and PowerPoint?  A lot of important work gets done with these tools every day.  Plus, software engineers do sometimes need to produce nicely-formatted documents, spreadsheets, and slides.  Don't most people use Office for that? 

The Microsoft Office suite is fine as far as it goes, but the ability to keep source files in distributed version control is a key advantage of command-line tools.  Version control with Git helps prevent data loss and enables integrating changes from multiple contributors, with no ambiguity about which copy of a file is the version of record. 

Word and PowerPoint can be easily replaced with `pandoc`, which accepts Markdown files and produces .pdf documents and slides.  Markdown is a plain-text format that is meant to be readable in itself, unlike HTML.

In turn, `sqlite` replaces Excel.  SQL scripts can be read into `sqlite` and then exported to .csv files, which can be shared with Excel-using colleagues. 

Here is some Markdown that can be turned into a .pdf document with `pandoc -s markdown.md -o document.pdf` or a slide deck with `pandoc -t beamer -s markdown.md -o slides.pdf`.  The slide deck contains a title slide and a content slide.

```markdown
---
title: A sample document
---

# Summary

`pandoc` converts Markdown to .pdf documents and slides!
```

The following SQL script can be read into `sqlite` and then exported to produce a .csv file with `sqlite3 test.db < test.sql; sqlite3 -header -csv test.db 'select * from table1;' > test.csv`.  It describes a table with a calculated column `c`, which gives the hypotenuse of a right triangle with two shorter sides `a` and `b`. 

```sql
create table table1(
    a real,
    b real,
    c real as (sqrt(power(a, 2) + power(b, 2)))
);

insert into table1 (a, b) values (1, 2), (3, 4);
```

Notably, both the Markdown file and the SQL script above are text files that can be kept in version control.

Of course, Excel offers plotting capabilities that `sqlite` can't duplicate.  That task can be covered by `gnuplot`, but that's a topic for another post.
