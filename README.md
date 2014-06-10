# Circuit Reveal

An extension of [Reveal.js generator](https://github.com/slara/generator-reveal). With specific styling for the CIRCUIT Conference.

## How to use CIRCUIT Reveal

Install:
* clone the repository
* make sure you have the [node.js](http://nodejs.org/) installed
* run the following in your repository folder
```
npm install
```
* follow the steps to install [the reveal-generator](#usage)
* run ``` bower install ```
* add your presentation information to the presentationInfo.json

```
{
    "presentationTitle"        : "Your Presentation Title Goes Here",
    "presentationDate"         : "Your Presentation date goes here eg (June 4th 2014)",
    "presentationHashTag"      : "#PresentationHashTag",
    "presentersName"           : "Your Name",
    "presentersTwitterHandle"  : "@TwitterHandle"
}
```

## Reveal.js generator

A [Yeoman](http://yeoman.io) generator for the awesome [Reveal.js](http://lab.hakim.se/reveal-js/) presentation framework.

## Usage

Install:  `npm install -g generator-reveal`

Start building your presentation.

After all files are created you can view your slides with `grunt`:

```bash
grunt server
```

Then, create further slides with:

```bash
yo reveal:slide more-content
```

See below for available [options](#options). When you want to export your presentation to some static HTML server, you can type `grunt dist` to have all your relevant files saved to the `dist` directory.

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

## Customisation

To change the options of the whole presentation, such as the theme used, transition 
effect, etc., consult the [Reveal.js documentation](https://github.com/hakimel/reveal.js#readme).
An important difference, though, is that you should not edit the `index.html`
file directly, as it gets overwritten as you add presentation content whenever a new grunt build is triggered. You should instead edit the `templates/_index.html` file, which is used as a template for the automatically generated `index.html`.

## License
[MIT License](http://en.wikipedia.org/wiki/MIT_License)
