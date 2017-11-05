# autodefensa-slides
Diapositives per els tallers d'autodefensa digital

Generat amb: https://github.com/slara/generator-reveal

## Installing and running

If you are checking out an existing presentation to do some work on it, make sure to install the required dependencies:
```
cd my-existing-project
npm install && bower install
```

Now you should be able to view the slides again with `grunt`:

```bash
grunt serve
```


## Generators

Available generators:

* [reveal:slide](#slide)

### Slide
Generates a Slide file.

Example:
```bash
yo reveal:slide "Slide Title"
```

Produces `slides/slide-title.html`:

```html
<h2>Slide Title</h2>

<p>This is a new slide</p>
```

And the slide filename will be added to your `slides/list.json` file.

```json
[
    "index.md",
    "slide-title.html"
]
```

#### Vertical Slides

In order to add vertical slides, you can nest an array inside `slides/list.json`

```json
[
    "index.md",
    [
        "vertical-html.html",
        "vertical-markdown.md"
    ],
    [
        "vertical-html-2.html",
        "vertical-markdown-2.md"
    ],
    "the-end.md"
]
```

#### Simple (Image) Slides

Sometimes you just want a slide with a background image. That's okay, a slide object does not need a filename.

```json
[
    "index.md",
    {
        "attr": {
            "data-background": "http://example.com/image.png"
        }
    }
]
```

#### Options

##### Markdown

Invoked with `--markdown`

```bash
yo reveal:slide "Slide Title" --markdown
```

Produces `slides/slide-title.md`


```markdown
## Slide Title

This is a new slide
```

##### Attributes

Invoked with `--attributes`

```bash
yo reveal:slide "Slide Title" --attributes
```

adds a slide `Object` with an `attr` key to your `slides/list.json` file. Attributes will be passed to `section` element containing the slide.

```json
[
    "index.md",
    {
        "filename": "slide-title.md",
        "attr": {
            "data-background": "#ff0000"
        }
    }
]
```

```html
<section data-markdown="slides/slide-title.md" data-background="#ff0000"></section>
```

##### Speaker Notes

Invoked with `--notes`

```bash
yo reveal:slide "Slide Title" --notes
```

Produces `slides/slide-title.html`:

```html
<h2>Slide Title</h2>

<p>This is a new slide</p>

<aside class="notes">
    Put your speaker notes here.
    You can see them pressing 's'.
</aside>
```

All three options maybe combined, e.g.

```bash
yo reveal:slide "Markdown Slide With Notes And Section-Attributes" --notes --attributes --markdown
```



## Resources

If your presentation requires specific resources that you would like included
with your project, place them in the resources directory.  These assets will be
included in the distribution and available for access at the path
`resources/asset_name.ext`.
