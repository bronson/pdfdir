## pdfdir

Turns a directory tree of PDFs into a single bookmarked PDF.

Bookmarks are the hierarchical table of contents you see in
most PDF readers.

Tested on Linux and Mac.


### Usage

If you arrange your PDF files in folders like this:

    book/01-Table of Contents.pdf
    book/02-First Generation/Mary Cunningham.pdf
    book/02-First Generation/Peter Cunningham.pdf
    book/03-Second Generation/John Mendell Cunningham.pdf
    book/99-Index.pdf

The "01-", "02-" prefixes determine the order of the chapters in the
final book.  They will not appear in the bookmarks.

Then run:

    $ pdfdir-join book

you will find the result in "book.pdf"


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

