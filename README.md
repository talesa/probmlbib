# Probabilistic ML Bibliography

I've adapted this model for shared bibliography management from the [OVAL](https://www.robots.ox.ac.uk/~oval/) & [VGG](https://www.robots.ox.ac.uk/~vgg/) groups, shout-out to [Leo Berrada](http://www.robots.ox.ac.uk/~lberrada/) for sharing this!

If you're my coauthor and you don't have time to fill this bibliography as intended please put your references into `dirty.bib`, I'll take care of them in due time.

## How do I use the shared bibliography in my workflow?

There are at least two ways.

The simpler way is to use [git submodules](https://blog.github.com/2016-02-01-working-with-submodules/), i.e. a repo inside a repo.
This seems to be easier if you collaborate with others on your manuscript since the bibliography is pulled together with your manuscript repo (despite being in a seperate repo).
Use `git submodule add git@github.com:talesa/probmlbib.git bibliography` to put this repo inside the repo with your manuscript. 
Then default way to use the bibliography is `\bibliography{bibliography/standardstrings,bibliography/bibliography,bibliography/dirty}` (surprisingly it seems to matter that there is not space after the commas!). 
After you modify the `*.bib` files, go inside the `bibliography` folder and add, commit & push changes to this repo (seperately from the main manuscript repo). 
Then go to your manuscript repo and add, commit & push the `bibliography` folder, just the information about bibliography repo commit id is kept.

The other, more fancy, but seemingly less practical when working with others, way is to set the environment variable `BIBINPUTS` to have latex look for the `*.bib` files in the right directory by default. 
For example, you can set `export BIBINPUTS=$HOME/workspace/probmlbib` if the git repository is in  `$HOME/workspace/probmlbib`.
Then the default way to use the bibliography is `\bibliography{standardstrings,bibliography,dirty}`.
The advantage of this method is that you don't need a submodule inside the manuscript repo.

## General Rules

 1. Name of bibentry: take the name of the first author, capitalize it and append
    the year of publication (e.g. `Gauss1821`, `Shannon1948`). If another entry exists under this name and year
    then break the tie by adding `a`, `b`, `c` etc at the end. For example,
    `Gauss1821`, then `Gauss1821a`, then `Gauss1821b`, then `Gauss1821c` etc.
    If you find that the new paper you want to add was published earlier
    in the year than a previous entry, the new paper (not the most recently
    published) still goes at the end.

 2. Find the correct place in `bibliography.bib` (order is alphabetic by bibref key)
    and insert your bibentry.

 3. Verify that the bibfile is still working (e.g. compile your LaTeX document) and commit the change.

## Style Guidelines:

  1. The author field must be in the form `{Surname1, FirstName1 and Surname2, FirstName2 and Surname3, FirstName3}`
  2. For the conferences, journals etc., use the journal id that links to a string in `standardstrings.bib`, `shortstrings.bib` or `longstrings.bib`.
     For example, `journal = neurips` will use the link `@string{neurips = "Advances in Neural Information Processing Systems"}` if you have just `\bibliography{standardstrings,bibliography}` in your tex file, or `@string{neurips = "NeurIPS"}` if you have `\bibliography{standardstrings,shortstrings,bibliography}` in your tex file, or the link `@string{neurips = "Advances in Neural Information Processing Systems (NeurIPS)"}` if you have `\bibliography{standardstrings,longstrings,bibliography}`. 
     Add new ids if they are not there yet.

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

* If you want to extract the citations needed (and not the whole database) for your document `mydoc.tex`, you can run `bibexport -o extracted.bib mydoc.aux` to obtain these citations in `extracted.bib`
