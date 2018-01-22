# remark_lectures

## To do

* Assets require `/remark_lectures/assets/` on GH Pages, but `/assets/` on localhost
* Create index pages for each folder

### Solution from Github:

Adapted from a response to [Issue #332 ](https://github.com/jekyll/jekyll/issues/332#issuecomment-18952908).

If you are using the standard URL for a GitHub Pages project (`username.github.io/project-name/`), here is one approach to the problem of locating assets within a Jekyll project.

In `\_config.yml`, set the `baseurl` option to `/project-name` where the project name is the name of the repository. Keep the leading slash and be sure to exclude any trailing slash.

Now you'll need to change the way you do links in your templates and posts, in the following two ways:

When referencing JS or CSS files, do it like this: {{ site.baseurl }}/path/to/css.css -- note the slash immediately following the variable (just before "path").

When doing permalinks or internal links, do it like this: {{ site.baseurl }}{{ post.url }} -- note that there is no slash between the two variables.

Finally, if you'd like to preview your site before committing/deploying using jekyll serve, be sure to pass an empty string to the --baseurl option, so that you can view everything at localhost:4000 normally (without /project-name getting in there to muck everything up): jekyll serve --baseurl ''

This way you can preview your site locally from the site root on localhost, but when GitHub generates your pages from the gh-pages branch all the URLs will start with /project-name and resolve properly.

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
