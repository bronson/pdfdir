## pdfdir

Turns a directory tree of PDFs into a single bookmarked PDF.

Bookmarks are the hierarchical table of contents you see in
most PDF readers.

Tested on Linux and Mac.


### Usage

If you arrange your PDF files in folders like this:

    book/01-Table of Contents.pdf
    book/02-First Generation/01-Mary Cunningham.pdf
    book/02-First Generation/02-Peter Cunningham.pdf
    book/02-First Generation/02-:more-notes.pdf
    book/03-Second Generation/01-John Mendell Cunningham.pdf
    book/99-Index.pdf

and run:

    $ pdfdir-join book

you will find the result in "book.pdf"

The PDF's table of contents will be automatically generated from the filenames:

    Table of Contents
    First Generation
      Mary Cunningham
      Peter Cunningham
    Second Generation
      John Mendell Cunningham
    Index

The "01-", "02-" prefixes determine the order of the chapters in the
final book and don't appear in the bookmarks.

Normally each filename is automatically added to the table of contents.
If you don't want this, adding a `:`  at the beginning of the filename
will keep it hidden (see 02-:more-notes.pdf above).


### Prerequisites

MacOS: brew install ghostscript
Linux: apt-get install ghostscript

And also Ruby.  Hopefully this is temporary.


### Verify PDFs

This package also includes some tools to help assemble the input files.
This will find corrupt PDFs:

    $ pdfdir-verify book

It uses Ghostscript to carefully process every page of every PDF file.
This is awfully slow.  You can specify --quick for a 10X speedup
at the risk of missing some obscure corruptions.


### Re-encode PDFs

If you're having trouble with encrypted or corrupt PDFs, try using
pdfdir-copy to duplicate your entire directory structure.  It takes
a while but, because it re-encodes each PDF, the result is sure to
be valid.

    $ pdfdir-copy book /tmp/book-fixed

