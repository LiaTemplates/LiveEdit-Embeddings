<!--

author:  André Dietrich

email:   LiaScript@web.de

version: 0.0.1

logo:    img/logo.png

comment: This document provides some examples for the usage of the LiaScript
         LiveEditor, which can be used to embed interactive code examples into
         your markdown documents.

@embed.edit
@embed_(edit,height: 80vh; min-width: 100%; border: 1px black solid,``````@0
``````)
@end

@embed.edit.style
@embed_(edit,@0,``````@1
``````)
@end

@embed.preview
@embed_(preview,height: 80vh; min-width: 100%; border: 1px black solid,``````@0
``````)
@end


@embed.preview.style
@embed_(preview,@0,``````@1
``````)
@end


@embed
@embed_(none,height: 80vh; min-width: 100%; border: 1px black solid,``````@0
``````)
@end


@embed.style
@embed_( ,@0,``````@1
``````)
@end


@embed_
<script run-once modify="false">
let code = `@'2`

code = btoa(unescape(encodeURIComponent(code)))

let embed ="@0"

if (embed=="preview" || embed=="edit") {
  embed += "/"
} else {
  embed = ""
}

'HTML: <iframe loading="lazy" style="@1" src="https://liascript.github.io/LiveEditor/?/embed/code/' + embed + code + '"></iframe>'
</script>
@end
-->

# LiveEdit-Embeddings

    --{{0}}--
Insert examples with the LiaScript LiveEditor. This allows you to create interactive code examples that can be edited and executed directly in the browser.

    --{{1}}--
Explore the following resources for more information and documentation:

     {{0-1}}
* See the GitHub version of this document
  [here...](https://github.com/LiaTemplates/LiveEdit-Embeddings)
* See the LiaScript version of this document
  [here...](https://liascript.github.io/course/?https://raw.githubusercontent.com/LiaTemplates/LiveEdit-Embeddings/refs/heads/main/README.md)

There are three ways to use this template.
The most straightforward approach is to use the `import` statement with the URL of the raw text-file from the master branch or any other specific branch/version.
Alternatively, you can directly copy the necessary code into the header of your Markdown document, as detailed on the [last slide](#implementation).
Finally, you can clone this project and customize it according to your needs.

                           {{2}}
1. Load the macros via

   `import: https://raw.githubusercontent.com/LiaTemplates/LiveEdit-Embeddings/refs/heads/main/README.md`

   to import the latest version, but keep in mind that the API might evolve. To load a specific version, use:

   `import: https://raw.githubusercontent.com/LiaTemplates/LiveEdit-Embeddings/refs/tags/0.0.1/README.md`

2. Copy the definitions into your Project

3. Clone this repository on GitHub


## `@embed`

    --{{0}}--
Within the head of the code-block simply add `@embed` to enable the LiveEditor for this code-block. The default height is set to `80vh` and the width to `100%`.


```` markdown
``` markdown @embed
# Hello World

This is a simple example that shows how to use the LiveEditor.
```
````

---

__Result:__

``` markdown @embed
# Hello World

This is a simple example that shows how to use the LiveEditor.
```

### `@embed.style`

    --{{0}}--
However, you can overwrite the default settings by using the `@embed.style` macro. The first parameter is the style that should be applied to the iframe.

```` markdown
``` markdown @embed.style(width: 100%; height: 50vh; border: 4px red solid)
# Hello World

... but this time a bit smaller ...
```
````

---

__Result:__

``` markdown @embed.style(width: 100%; height: 50vh; border: 4px red solid)
# Hello World

... but this time a bit smaller ...
```


## `@embed.edit` & `@embed.edit.style`

    --{{0}}--
If you want to display an editable code-block, you can use the `@embed.edit` or `@embed.edit.style` macro.
The user can still change the visualization to the preview mode.


```` markdown
``` markdown @embed.edit.style(height: 300px; width: 100%)
# Hello World

This is a simple example that shows how to use the LiveEditor.
```
````

---

__Result:__

``` markdown @embed.edit.style(height: 300px; width: 100%)
# Hello World

This is a simple example that shows how to use the LiveEditor.
```

## `@embed.preview` & `@embed.preview.style`

    --{{0}}--
To be complete, you can also directly show the preview and let the user click onto the shared or edit view.

```` markdown
``` markdown @embed.preview.style(height: 400px; width: 100%)
# Hello World

This is a simple example that shows how to use the LiveEditor.
```
````

---

__Result:__

``` markdown @embed.preview.style(height: 400px; width: 100%)
# Hello World

This is a simple example that shows how to use the LiveEditor.
```

## Implementation

    --{{0}}--
This macro encodes the entire content of the code-block into a Base64 encoded string and adds it to an the URL of the LiveEditor, as it is depicted in the macro `@embed_`.
This macro is only a helper, which is used by the others with predefined parameters.


```````` html
<!--
@embed.edit
@embed_(edit,height: 80vh; min-width: 100%; border: 1px black solid,``````@0
``````)
@end

@embed.edit.style
@embed_(edit,@0,``````@1
``````)
@end

@embed.preview
@embed_(preview,height: 80vh; min-width: 100%; border: 1px black solid,``````@0
``````)
@end


@embed.preview.style
@embed_(preview,@0,``````@1
``````)
@end


@embed
@embed_(none,height: 80vh; min-width: 100%; border: 1px black solid,``````@0
``````)
@end


@embed.style
@embed_( ,@0,``````@1
``````)
@end


@embed_
<script run-once modify="false">
let code = `@'2`

code = btoa(unescape(encodeURIComponent(code)))

let embed ="@0"

if (embed=="preview" || embed=="edit") {
  embed += "/"
} else {
  embed = ""
}

'HTML: <iframe loading="lazy" style="@1" src="https://liascript.github.io/LiveEditor/?/embed/code/' + embed + code + '"></iframe>'
</script>
@end

-->
````````