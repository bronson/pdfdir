## pdfdir

Turns a directory tree of PDFs into a single bookmarked PDF.

Bookmarks are the hierarchical table of contents you see in
most PDF readers.


### Usage

If you arrange your PDF files in a hierarchy, like this:

    book / 01-Introduction.pdf
    book / 02-Engine
    book / 02-Engine / 01-Coolant.pdf
    book / 02-Engine / 02-Freeze Plugs.pdf

    (the "01-", "02-" prefixes determine the order of the chapters in the
    final book.  They will not appear in the bookmarks.)

Then run:

    $ pdfdir-join book

you will find the result in "book.pdf"

Too easy!


### Prerequisites

Ghostscript

MacOS: brew install ghostscript
Linux: apt-get install ghostscript


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

