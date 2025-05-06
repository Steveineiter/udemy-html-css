# udemy-html-css

Its also amazing that i can use VIM in this project :D see my shell-setup readme for commands.
We are using prettier linter.

## VSC extensions:

- prettier
- image preview
- color highlight (for CSS)
- auto rename tag
- live server

## HTML notes:

1. We should use only ONE h1 tag.
2. We should NOT use \<b> for bold text but \<strong> in HTML5. This is called semantic HTML.
3. We should not use \<i> for italic, but \<em> in HTML5, reason as above.
4. We should add lang and charset, but most likely we will do this automatically.
5. We should use \<a> tag for anchoring (eg to set links). The href property really makes an anchor a link. With href="#" we can specify links without having a link, sort of a placeholder.
6. We should group elements. Eg using \<nav> for navigation bar, and stuff after by eg sections. Or for top part of page using \<header> and \<article> for rest. Nav, header, article, aside, footer,... is used in semantic HTML / a part of it.
7. Semantic is the concept of not thinking how an element gets rendered and looks on the page, but what the element means and what it stands for. Eg using strong instead of bold, which means this is a strong content, instead of that it looks bold. Or nav tells us that it is a navigation (has no technical meaning, eg no difference of using div / nothing will visually change. Its just a box without meaning.) This is one of the largest differences of HTML5. We could also use div instead of p, they all just create boxes (but with p its more readable through semnatics) aka we could build the whole page with divs xD.
8. Semantic stuff is nice for SEO (they understand structure) and extremly important for accessibility (eg better screenreaders). Also IMO it makes the code more readable. This encodes what this elements mean and what they stand for.
