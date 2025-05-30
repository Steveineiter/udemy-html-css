# udemy-html-css

Its also amazing that i can use VIM in this project :D see my shell-setup readme for commands.
We are using prettier linter.

## Important notes/thoughts

- I think i should always optimize for chrome (since opera and edge are chromium based). Aka if it works on chrome it should work everywhere as well sort of. I think chromium and safari are 90% of user base => **optimize for chromium and safari**.

## VSC extensions:

- prettier
- image preview
- color highlight (for CSS)
- auto rename tag
- live server

## HTML fundamentals notes:

1. We should use only ONE h1 tag.
2. We should NOT use \<b> for bold text but \<strong> in HTML5. This is called semantic HTML.
3. We should not use \<i> for italic, but \<em> in HTML5, reason as above.
4. We should add lang and charset, but most likely we will do this automatically.
5. We should use \<a> tag for anchoring (eg to set links). The href property really makes an anchor a link. With href="#" we can specify links without having a link, sort of a placeholder.
6. We should group elements. Eg using \<nav> for navigation bar, and stuff after by eg sections. Or for top part of page using \<header> and \<article> for rest. Nav, header, article, aside, footer,... is used in semantic HTML / a part of it.
7. Semantic is the concept of not thinking how an element gets rendered and looks on the page, but what the element means and what it stands for. Eg using strong instead of bold, which means this is a strong content, instead of that it looks bold. Or nav tells us that it is a navigation (has no technical meaning, eg no difference of using div / nothing will visually change. Its just a box without meaning.) This is one of the largest differences of HTML5. We could also use div instead of p, they all just create boxes (but with p its more readable through semnatics) aka we could build the whole page with divs xD.
8. Semantic stuff is nice for SEO (they understand structure) and extremly important for accessibility (eg better screenreaders). Also IMO it makes the code more readable. This encodes what this elements mean and what they stand for.
9. the first file should always be called index.html, this is convention.

## CSS fundamentals notes:

Documentation is https://developer.mozilla.org/en-US/ (MDN web doc) nice.

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
13. In Chromium inspect on the left side are HTML elements and on the right side we have the CSS styles. In styles we can click on :hov an change the state (eg of \<a> elements). Also i think the CSSOM is build from bottom up, aka things which are on the top overwrite those from the bottom.
    - Really nice to try things out without changing our code (eg to try out different CSS priorities)
14. We can have conflicting selectors (eg different rules which select the same element). Then we have different priorities which builds the CSSOM. See resolving slide. If we have same priority last selector in code applies. Priority is: External styles with Universal selector (\*), Element selector (p, div, li, ...), Class (.) or pseudo-class(:) selector, ID (#) selector, Internal styles (same priorities of id, class, etc), Inline styles (which we shouln't do), declarations marked !important (basically a hack, should also never be used - means our structure is too complex if we can't figure out why it won't work).**NOTE** all selectors will be applied, aka the priority is only important in case where we change the same property (eg font-size)
    - So normally we only have an external style sheet and thus in practice: _Universal selector < Element selector < Class selector (with last applied in code is more important)_
    - If we hover over the selector we can see the priority as well
    - More complex selectors have a higher number (if we hover over in VSC) which means they will have a higher priority first (higher is better)
15. we can also add 2 classes (class="foo bar")
16. We can say that inherited values do have the lowest properties. Need to check out if thats true (eg inherited from a class tag) - nope xD Most of the inherited properties are related to text (font-family, font-size, color, ...) but NOT things like border-top
17. Universal selector applies to all elements but won't be inherited. Styles which are eg in body are on the ohter hand inherited.
18. **Best practices** see challenge file in section_3(item-69.html and item-69.css). Most of the times he uses classes (only exception, if its for everything eg font family), and for anchors he styles each part individual (so instead of a {color} he uses a:link {color}). Also he adds seperators (eg PRODUCT, PRODUCT DETAILS, ...) as comments.
    - Also it's really nice to just inspect elements and then try stuff out (eg i had no clue how to style a button, but with inspecting it and playing around with the values it was quite straight forward)
    - Again, don't use eg li directly but eg class tag of ol/ul and then li tag. aka .foo li (decendet selector). I think thats important!
19. Box Model is like a painting. We have content, border, padding, margin and fill area (fills all except margin, eg with a background color). On heihgt and width calculation we have to keep in mind the padding and border (aka width = left border&padding + width + right padding&border). This is by default, but we can change this (since it might not make sense in our usecase).
    - He likes to keep big boxes on top of CSS file.
    - See box model on bottom of styles in inspect for color mapp (eg padding is green)
    - For **creating vertical space** its often common to only add a margin to the bottom. We should stick to one tho (either use only top or bottom, but he thinks only add to bottom makes more sense). Thats because if we mix it up it might be hard to design it as we want (eg 50 top and 30 bot of previous element will not be 80 apart but only 50 called _collapsing margins_)
    - Currently we use numbers for margin/padding etc sort of by feeling/at random. Later we will have a system for this.
    - If we need space inside of element (mostly usefull if we use background color), if we need space outside or between elements always use margin. For vertical space use bottom margin as discussed above.
    - **Inline block** advantages: combines best of both worlds: Occupies only content's space and cause no line break from inline, box-model applies as showed from box model. Neat if we want to display elements side by side.
20. To center we need to have an container for everything. Since it has no sematnic meaning we can use a div for that. If we set a width then, children can only be as large as the width of this container.
21. We have inline boxes (eg strong) and block level boxes (eg body, header, footer, p, h2, ... - use 100% of parents width). Block level boxes are stacked vertically one after another by default.
    - Inline elements only occupies space necessary for its content (eg em, strong, a, img, button, ...), left and right paddings & margins do apply tho.
    - **Its important** to keep that in mind.
    - we can change this with the display property. Altough if we use this it's often a hack. Sometimes it makes sense tho.
    - There is a 3. type: Inline-Block boxes (look like inline from outside, behave like block level on inside.) This combines best properties of both. One case is eg for the nav bar we used for links.
    - Images behave like inline-block elements.
    - Most of the times we do not use display property!
22. We should **not use fixed numbers** for element heights.
23. We can use normal flow or absolute positioning. Normal flow is default with position: relative. For absolute position we have position: absolute (might overlap). We place an element relative to another container (top, right, ...) If we do not specify, its default relative to view point (aka top: 0, left: 0 results in beeing in upper left corner)
    - We have to **set postion:relative** of parent element where we want it to appear. This is sort of telling the absolute element "hey, be relative to me" altough they are relative by default. So it goes up and up of parents until something has position: relative; ("hey, be relative to me") else it uses the viewpoint.
    - **Don't use absolute** to often! We only use this for specific elements, as eg the like button.
24. Siblings are children of the same parent. Adjacent siblings are the very next sibling. Aka the sibling which comes right after it. We do this with eg h3 + p (so the + operator)
25. after and before are some of the most important pseudo-elements (used for **small adjustments** if we don't want to add a whole new element in HTML) its also good practice to set this to display: inline-block
26. **Debugging** in CSS/HTML is pretty much checking out the rendered page. I guess using inspect is nice as well.
    - Often its about the tags (eg forgetting to close aside) which then is harder to find later. We can then use a **HTML validator (always nice tho)** to validate our html (eg validator.w3.org).
    - Also its nice to compare files (diff, eg previous version and buggy one, or my solution and his solution) we can use inbuilt of IDE or use diffchecker.com.
    - Another bug cause are often with selectors. Eg we write a class selector on bottom of file and later a nested element selector. Then its great to check out the CSSOM in inspect. Also AVOID complex selectore (will avoid bugs like those). Eg use classes most of the time as we did in the challenge.
    - If we have no CSS in our rendered page, most of the times if we messed up the link/import from CSS file to HTML file.
    - In a nutshell, check our rendered page, inspect, check code, use tools.

## Layouts: Flotas, Flexbox, and CSS Grids

1. Flexbox and CSS Grids are the most modern approach.
2. Layouts provide visual strcuture, into which we place content. This is one of our main jobs.
3. We create a visual layout to not have them one after another (normal flow) which looks boring and harder to understand.
4. We have page and component layout.
5. Float layouts are old way, are getting outdated fast so might be in legacy systems. CSS Grid is nice if we have a 2-dimensionald grid. Thus **Flexbox is nice for component and CSS Grid for Page layout**.
6. If element are floats its as the elements are not on the page / are removed. Thats why eg background colors might get messed up with floats. This is called _collapsing element_. They are not a positioning argument.
7. If we create layouts its often nice to give them background colors, so that we see them easier on the page.
8. If we have too large widths of elements (eg container has 1200px, float1 has 800 float2 450) the design will get messed up. Then we have to change the box-model (default is box-sizing: content-box) by using **box-sizing: border-box**. This is cool because we can specify how large the box should be. He stated that almost any frontend-engineer uses this, since it makes much more sense. Becuase the calculations are much more simpler (no border, no padding) thus width=width, height=height. This makes our life much easier. Keep in mind that margin is NOT included tho.
   - Good pratice to have it in all-selector \* {}
9. We **don't need calulcations** etc anymore as soon as we use flexbox. Looking forward to that \<3 xD
10. We also aren't too deep into how floats work since they are quiet obsolote xD.

### Flexbox

1. have width as much they need, height of the highest flex-item within a given parent by default. But we can use eg align-items:center
2. Flexbox REALLY powerful. We can do things with one line which else would need quite a lot of code and trial and error / calculations to get it right.
