# Mercury Editor

Mercury Editor is a fully featured editor much like TinyMCE or CKEditor, but with a different usage paradigm.	It expects that an entire page is something that can be editable, and allows different types of editable regions to be specified.	It displays a single toolbar for every region on the page, and uses the HTML5 contentEditable features on block elements, instead of iframes, which allows for CSS to be applied in ways that most other editors can't handle.

Mercury has been written using CoffeeScript and jQuery for the Javascript portions.


## Browser Support

Mercury has been written for the future, and thus doesn't support legacy browsers or browsers that don't follow the W3C specifications for content editing.	Any browser will be supported if they support the W3C specification in the future, but there aren't plans for adding support for alternate implementations at this time.

Supported Browsers:

- Chrome 10+
- Safari 5+
- Firefox 4+


## The Story

I was looking for a fully featured editor that didn't use iframes, and there weren't any decent ones.	My primary goal was to have areas that were editable, but that also allowed CSS to flow naturally.	A few have cropped up since then (Aloha Editor for instance), and as good as they are, none had all the features I was looking for.

Mercury was written to be as simple as possible, while also providing an advanced feature set.	Instead of complex configuration, we chose a mix of configuration and code simplicity, which should give you a much better chance at customizing Mercury to suit your exact needs.	This doesn't mean there's not configuration, and what's there provides much of what you'll need, but efforts were taken to keep it simple and powerful.

Even though it's a great editor, Mercury Editor may not be the best for your needs (based on browser support, javascript library, etc.) so here's a list of some other editors that you might want to check out:

- [Aloha Editor](http://www.aloha-editor.org/)
- [jHtmlArea](http://jhtmlarea.codeplex.com/)
- [MarkItUp](http://markitup.jaysalvat.com/home/)
- [TinyMCE](http://tinymce.moxiecode.com/)
- [CKEditor](http://ckeditor.com/)
- [NicEdit](http://nicedit.com/)


## Features

The feature list is actually pretty long, so here's a short list that need highlighting.

- Previewing: Preview content while you're working to see exactly how it'll look.
- Link Tools: Insert and edit links, including TOC/Bookmark links.
- Media Tools: Insert and edit images, youtube videos, and vimeo videos.
- Image Uploading: Drag images from your desktop and they'll be automatically uploaded and inserted.
- Table Editing: Advanced table editing and creation.
- Snippets: Insert and edit predefined and reusable bits of markup/code using drag and drop.
- Notes: Attach notes to any page and communicate with other content authors.
- Colaborative Editing: Edit any page that others are editing at the same time and see their changes in real time.

## Usage

### Get Started

	git clone git://github.com/balupton/mercury.git
	cd mercury
	npm install -g coffee-script
	npm install
	coffee server.coffee

Then open [http://localhost:3000/src/demo/](http://localhost:3000/src/demo/)


### Implementation

Under heavy refactoring, refer to `src/demo` for the latest.


### Building

	cd mercury
	coffee buildr.coffee


## Region Types

### Editable

Editable Regions are HTML markup, and use the HTML5 contentEditable feature.	This is the core of what Mercury is about, and provides the most flexibility and visual representation of what the content will look like when saved.

### Markupable

These regions are based on Markdown syntax (specifically the github flavored version), and isn't as full featured as the editable region type -- primarily because markdown is meant to be simple, so to keep it such you can't do things like set colors etc.	This region type is super useful if you want to keep the markup clean and simple.

### Snippetable

Snippetable regions only allow snippets.	There isn't any content editing in these regions, but snippets can sometimes be the way to go with complex markup and functionality.	Snippets are basically chunks of reusable markup, that can be defined by a developer and placed into content regions later.	More on this below.


## Snippets

Snippets are reusable and configurable chunks of markup.	They can be defined by developers, and then placed anywhere in content regions.	When you drag a snippet into a region you'll be prompted to enter options, and after entering options the snippet will be rendered into the page as a preview.	Snippets can be dragged around (in snippetable regions) and edited or removed.

Mercury does very little to save content and snippets for you, but it does provide the ability to load snippets from your own storage implementation.	Here's an example of loading existing snippet options back into Mercury.

``` coffeescript
$ ->
	$('body').bind 'mercury-ready', ->
		mercuryWindow.Mercury.Snippet.load {
			snippet_1: {
				name: 'example'
				options: {
					'options[favorite_beer]': "Bells Hopslam"
					'options[first_name]': "Jeremy"
				}
			}
		}
```


## Project Details

### WYSIWYG Editors Suck

They just do.	Which as I've learned, is primarily due to the browser implementations.	Don't get me wrong, what the browsers have implemented is amazing, because it's hard stuff, plain and simple.	But if you're expecting a WYSIWYG editor to solve all your content problems you're wrong.	A better perception is that it will solve many of them, but shifts some into a new area.

With that being said, Mercury tries to solve many of those issues and succeeds to a great degree, but alas, it's nearly impossible to address everything, and the browsers don't expose enough to fix some things.	This is true for every editor that I've looked into as well.

It's important to understand this, and the details are more suited for long nerdy blog posts, so they won't be covered here.

### The Code and Why

#### CoffeeScript

Mercury has been written entirely in CoffeeScript because it simplifies a lot of the patterns that are used, and allows for very readable code.	The goal was to provide good readable code that could be adjusted based on need, instead of a complex configuration that makes the code harder to understand and tweak.

#### jQuery

jQuery was used as the javascript library, but is primarily used for the selectors, traversing, and manipulating the DOM.	Chaining is kept to a minimum for readability, and even though much of Mercury could've been written as jQuery plugins, it was not.


### Specs / Integration Tests

Under heavy refactoring.


## License

Licensed under the [MIT License](http://creativecommons.org/licenses/MIT/)
Copyright 2011 [Jeremy Jackson](https://github.com/jejacks0n)

### Contributors

- [Benjamin Lupton](https://github.com/balupton)