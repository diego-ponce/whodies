# WHODIES

A `whoami` but quotes from [Stephen Levine](https://en.wikipedia.org/wiki/Stephen_Levine_%28author%29)

## Quickstart

Web enabled
* todo

Running locally

* download whodies.txt (e.g. `curl ... > ~/whodies.txt`)
* run `alias whodies="cat <path/to/text> | shuf -n 1"` (or add to your `.bashrc` for persistence on your terminal)

## Do it yourself

* Inspired by excellent [YouTube tutorial from Nixcasts on Wikidate](https://www.youtube.com/watch?v=NYGI5xh4Llc&t=458s)
* Data from [AZQUOTES](https://www.azquotes.com/author/18346-Stephen_Levine)
* Uses [`w3m`](https://www.mankier.com/1/w3m) to easily parse the html
* `sed` to parse other content
* `shuf` to randomly select a line to quote
* tested in Linux, will update for MacOS

### get a random quote from a random page from the Stephen Levine Quote Page

`shuf -i 1-4 -n 1 | xargs -I {} w3m -cols 9999 -dump https://www.azquotes.com/author/18346-Stephen_Levine?p={} | sed -n '/\[quote-/,/INS/ p' | sed -n 's/^.*• //p'`

### get all 4 pages of Stephen Levine Quotes

`for i in $(seq 1 4); do w3m -cols 9999 -dump https://www.azquotes.com/author/18346-Stephen_Levine?p=${i} | sed -n '/\[quote-/,/INS/ p' | sed -n 's/^.*• //p'`
