# ``csvprint``

[![Build Status](https://travis-ci.org/vegarsti/csvprint.svg?branch=master)](https://travis-ci.org/travis-ci/travis-web)

A command-line utility for pretty printing csv files and converting to other formats.

## Installation

If Python 3 with the package manager pip is installed, doing `pip3 install csvprint` in your terminal should do the trick.

## Usage

`csvprint [filename]` prints a formatted table if `filename` is a comma separated file.

```
» cat imdb.csv
Title,Release Year,Estimated Budget
Shawshank Redemption,1994,$25 000 000
The Godfather,1972,$6 000 000
The Godfather: Part II,1974,$13 000 000
The Dark Knight,2008,$185 000 000
12 Angry Men,1957,$350 000

» csvprint imdb.csv
Title                  Release Year Estimated Budget
Shawshank Redemption   1994         $25 000 000
The Godfather          1972         $6 000 000
The Godfather: Part II 1974         $13 000 000
The Dark Knight        2008         $185 000 000
12 Angry Men           1957         $350 000
```
You can also pipe output from other programs to `csvprint` to format the output:

```
» cat imdb.csv | csvprint
Title                  Release Year Estimated Budget
Shawshank Redemption   1994         $25 000 000
The Godfather          1972         $6 000 000
The Godfather: Part II 1974         $13 000 000
The Dark Knight        2008         $185 000 000
12 Angry Men           1957         $350 000
```
## Options

Command       | Result
:-------------|:-------------------------------------------------------------
`--markdown`  | print as markdown
`--latex`     | print as latex table
`--header`    | add header decoration around the first line
`-p [n]`      | add a padding of `n` spaces for each column, on both sides
`-s 'char'`   | file is delimited by `char` (instead of comma), `tab` for tab
`-d [string]` | specify the string to separate columns
`-j`          | specify justification (left or right) - see examples below
`-h`          | print help message

## Justification example

There are three options for specifying justification. One can use `l` or `r` for justifying all cells to the left or right, respectively. One can also specify a distinct justification option for each column. Then the number of options will need to match the number of columns.

```
» csvprint imdb.csv -j l r r
Title                  Release Year Estimated Budget
Shawshank Redemption           1994      $25 000 000
The Godfather                  1972       $6 000 000
The Godfather: Part II         1974      $13 000 000
The Dark Knight                2008     $185 000 000
12 Angry Men                   1957         $350 000
```

## Markdown example

Markdown output also supports left and right justification.

```
» csvprint examples/imdb.csv --markdown -j l r r
Title                  | Release Year | Estimated Budget
:----------------------|-------------:|----------------:
Shawshank Redemption   |         1994 |      $25 000 000
The Godfather          |         1972 |       $6 000 000
The Godfather: Part II |         1974 |      $13 000 000
The Dark Knight        |         2008 |     $185 000 000
12 Angry Men           |         1957 |         $350 000
```

When rendered as HTML, this looks like

Title                  | Release Year | Estimated Budget
:----------------------|-------------:|----------------:
Shawshank Redemption   |         1994 |      $25 000 000
The Godfather          |         1972 |       $6 000 000
The Godfather: Part II |         1974 |      $13 000 000
The Dark Knight        |         2008 |     $185 000 000
12 Angry Men           |         1957 |         $350 000

## Testing

Run ``pytest`` while in the root directory of this repository.
