Title: This one weird trick (brace expansion) simplifies file manipulation in the shell
Date: 2024-10-06
Category: bash

File manipulation in Windows or Mac OS is simple and appealingly visual.  To rename a file, we just right-click or double-click on the file's icon and type the new name.  Moving files is only slightly harder and involves dragging the file from one folder to another.

By comparison, file manipulation in the shell can feel like a lot of work.  Of course, the `mv` command renames and moves files, and the `cp` command copies files.  These commands are simple enough to use when the source and destination files are in the present working directory, but often one or both files are somewhere else.  For example, renaming a file from the root of a git repository might involve `mv src/services/templateService.ts src/services/adminService.ts`.  Here, `src/services/` is duplicated between the originating and destination paths, which means extra typing.

Brace expansion provides a way to avoid this issue.  In brace expansion, we put multiple comma-separated options between curly braces.  With brace expansion, the preceding example becomes `mv src/services/{template,admin}Service.ts`.  We now have to type `src/services/` only once.

Both `mv` and `cp` expect two arguments; how does brace expansion supply them?  We can examine the results of brace expansion with the `echo` command.  Continuing our example, `echo src/services/{template,admin}Service.ts` gives `src/services/templateService.ts src/services/adminService.ts` -- the first and second arguments to `mv`.

Because `cp` takes only one destination file at a time, making multiple copies of a file requires combining a loop with brace expansion.  `for newfile in src/services/{contact,payment}Service.ts; do cp src/services/templateService.ts "$newfile"; done;` creates two copies of `templateService.ts` with appropriate names. 
