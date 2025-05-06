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
9. the first file should always be called index.html, this is convention.

## CSS notes:

1. We style elements by using selector (h1) with and declaration block which has multiple declarations/styles which consists of properties (font-size:) and values (20pf) inside.
2. We have 3 ways to implement CSS: Inline, Internal, External. Inline should never be used tho. We don't want to entangle html and css - we want to seperate it (seperation of concerns). Internal will bloat our code so external (aka having a own css file) might be the best approach, escepially if we have large css parts (eg 500 lines).
3. We import the CSS file with \<link> element (only purpose to connect html to css, might be confusing why we dont use this for links)
4. h1 doesnt has to be the largest one, we only care of semantics not how it looks on page.
5. bad practice to set eg font family in each element seperately. For that we can combine them. Also its good practice to use classes and IDs for selectors.
6. IDs are only allowed once. If we want to reuse them we need classes. **In real world we always use classes to be more robust**, becuase first using id then classes might lead to bugs. Thus we should **ALWAYS** use classes, also if we only use the code once.
7. CSS convention is to use kebap-case.
8. Colors in CSS: Often we use RBG/RGBA or Hexadecimal notation. (The RGBA a = alpha which is pretty much the saturation, aka at 0 its fully transparent) Hexadecimal is pretty much the same as RGB but shorter. Thus **in practice** we mostly use hexadecimal anf RGBA if we need transparancy. In hexadecimal we can write in shorthand notation if paris are the same (eg \#444444 => \#444)
9. Again we want to define colors in as little places as possible (aka using list selectors)
10. I guess firstly we style the component (eg header, p, aside, ...) and if this causes a unwanted behaviour THEN we add the class tag.
11. Pseudo classes are especially usefull for cases where child elements are the same (eg in ol or ul the li are always the same) but not if we mix child elements in classes (eg as with article p ). Also they are nice to style hypertext.
12. We shouln't style \<a> directly, but with a pseudoclass (eg a:link)
