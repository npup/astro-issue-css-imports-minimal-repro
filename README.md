# CSS import with relative path not working consistently as expected

Checkout and install

    git clone git@github.com:npup/astro-issue-css-imports-minimal-repro.git
    cd astro-issue-css-imports-minimal-repro
    npm i

## Dev mode, working

Start dev server:

    npm start

Point browser to http://localhost:3000/

Text 1 is green, text 2 is blue, as expected.

## Built mode, not working

Build and serve `./dist` with some help from python:

    npm run serve

Point browser to http://localhost:3001/

Text 1 is green, text 2 is unstyled (not expected).

It seems the built css file in `.dist/_astro/` (which is referenced from the HTML) still has the original relative import path in it (`./text.css`), so not able to find the actual import (which would now be `/style/text.css`).

