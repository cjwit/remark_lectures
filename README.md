# remark_lectures

## To do

* Assets require `/remark_lectures/assets/` on GH Pages, but `/assets/` on localhost
* Create index pages for each folder

### Solution from Github:

Adapted from a response to [Issue #332 ](https://github.com/jekyll/jekyll/issues/332#issuecomment-18952908).

If you are using the standard URL for a GitHub Pages project (`username.github.io/project-name/`), here is one approach to the problem of locating assets within a Jekyll project.

In `\_config.yml`, set the `baseurl` option to `/project-name` where the project name is the name of the repository. Keep the leading slash and be sure to exclude any trailing slash.

To create relative links to assets (Javascript or CSS files, images, videos, etc.), reference them using the `site.baseurl` variable: `{{ site.baseurl}}/path/to/file.jpg`. Do not forget the slash between the variable and the rest of the file path.

Permalinks or internal links to posts should use `{{ site.baseurl }}{{ post.url }}` with no slash between variables.

To work using localhost, override the baseurl option with an empty string. Run `jekyll serve` from the command line with the following:

```
jekyll serve --baseurl ""
```

The required folder for the built page on GitHub Pages should not interfere with the localhost:4000 version of the page. It also allows GitHub to properly build the live page.

### Embedded local video

560x420 dimensions work well

```html
---

class: middle, center

<video width="560" height="420" controls>
    <source src="Ain't That A Shame.mp4" type="video/mp4">
</video>

### iframe video test

---
```

### Background image CSS

code for html page header (or presentation layout in jekyll):

```css
.remark-slide-content {
	background-size: contain;
}
```

### Other useful CSS for html/layout header

Drawn from the Remark.js demo slides

#### Two column layout

```css
.left-column {
	color: #777;
	width: 20%;
	height: 92%;
	float: left;
}
.left-column h2:last-of-type, .left-column h3:last-child {
	color: #000;
}
.right-column {
	width: 75%;
	float: right;
	padding-top: 1em;
}
```

#### Inverse layout

```css
.inverse {
	background: #272822;
	color: #777872;
	text-shadow: 0 0 20px #333;
}
.inverse h1, .inverse h2 {
	color: #f3f3f3;
	line-height: 0.8em;
}
```

#### List item and sub-list styles

Changes color for sub-list and gives some margin spacing to improve the layout. Increased text size for visibility

```css
.remark-slide-content {
	font-size: 24px;
}
li {
	color: black;
	margin-top: 1em;
	list-style-type: disc;
}
li > ul > li {
	color: #777872;
	margin-top: 0.3em;
	list-style-type: disc;
	font-size: 20px;
}
```
