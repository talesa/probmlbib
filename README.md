# OVAL Bibliography

Adapted from the VGG model.

## General Rules

 1. Name of bibentry: take the name of the first author, capitalize it and append
    the year of publication (e.g. `Gauss1821`, `Shannon1948`). If another entry exists under this name and year
    then break the tie by adding `a`, `b`, `c` etc at the end. E.g.
    `Gauss1821`, then `Gauss1821a`, then `Gauss1821b`, then `Gauss1821c` etc.
    If you find that the new paper you want to add was published earlier
    in the year than a previous entry, the new paper (not the most recently
    published) still goes at the end.

 2. Find the correct place in `oval.bib` (order is alphabetic by bibref key)
    and insert your bibentry.

 3. Verify that the bibfile is still working (e.g. run the `checkbib.sh`
    script or compile your LaTeX document) and commit the change.

## Style Guidelines:

  1. The author field must be in the form `{Surname1, FirstName1 and Surname2, FirstName2 and Surname3, FirstName3}`
  2. For the conferences, journals etc., use the journal id that links to a string in `shortstrings.bib` or `longstrings.bib` (e.g. `journal = nips` will use the link `@string{nips = "NIPS"}` if you have `\bibliography{shortstrings, oval}` in your tex file, or the link `@string{nips = "Advances in Neural Information Processing Systems"}` if you have `\bibliography{longstrings, oval}`). Add new ids if they are not there yet (at the moment there are mostly computer vision venues since it comes from the VGG).

  3. Do not use tabs.

  4. Use lower case for the fields (e.g. `year =`, not `YEAR =`).

## Type of Entries

We give the main types of entries and their mandatory fields.

* `@Article` (conference / journal articles):
    * `author`
    * `title`
    * `journal`
    * `year`
* `@Book` (books):
    * `author`
    * `title`
    * `publisher`
    * `year`
* `@Manual` (tech reports / dataset documentation / software documentation):
    * `author`
    * `title`
    * `year`

NB: In some corner cases, one might need to use more specific entries, e.g. `InCollection` to cite a particular part of a book. In these cases, follow the `bibtex` rules for the mandatory entries.

## Tips

* You can set the environment variable `BIBINPUTS` to have latex look for the `.bib` file in the right directory by default. For example, you can set `export BIBINPUTS=$HOME/workspace/bibliography` if the git repository is in  `$HOME/workspace/bibliography`.

* If you want to extract the citations needed (and not the whole database) for your document `mydoc.tex`, you can run `bibexport -o extracted.bib mydoc.aux` to obtain these citations in `extracted.bib`


