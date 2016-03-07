# &lt;fullscreen-api&gt;

_A simple Polymer based Web Component wrapper for the HTML5 full screen API._

Please refer to the <a href="https://vguillou.github.io/webcomponents/fullscreen-api/">component page</a> for more informations.

* **fullscreen-api**: The most flexible, comes without UI but with bindable attributes. Ideal when you need to dynamically set the element to display fullscreen (an image gallery for example).
* **fullscreen-icon-button**: Prepackaged material icon-button. Drop it on your page, tap it and it works. 

Both elements let you define what to display in full screen mode
(via the `target` attribute) and toggle normal/full screen
mode by calling the `toggleFullscreen()` method.

Note that this method MUST be triggered directly by user interaction
(typically in a native `onclick` or Polymer's `on-click` handler).
If no `target` is set, the whole page (more specifically
`document.documentElement`) will be displayed full screen.

The element also provides 2 read-only flags as attribute:
* `fullscreenAvailable`: set to `true` if the browser supports
   HTML5's full screen API (Safari on iOS does not).
* `fullscreen`: set to `true` if an element is currently displayed in
   full screen mode.

### Attributes

* **target** :
The element to display full screen (document.documentElement by default),
or the selector to use to automatically find that element.
Note that changing the target while in full screen mode will not
have any effect, as toggling between display modes MUST be
triggered by user interaction.

* **fullscreen** :
Read-only flag (boolean) indicating if an element is being displayed full screen.

* **fullscreenAvailable** :
Read-only flag (boolean) indicating if full screen mode is available on the browser
(Safari on iOS does not support it).

### Methods

* **toggleFullscreen()** :
Toggle between full screen and normal display mode.
MUST be triggered directly by user interaction (typically in a native 'onclick'
or Polymer's 'on-click' handler).

* **exitFullscreen()** :
Exit full screen mode (if toggled).

## Example

* **fullscreen-api**

```html
<template is="dom-bind">
	<fullscreen-api id="fsapi" fullscreen-available="{{fullscreenAvailable}}"></fullscreen-api>

	<button type="button" onclick="goFullscreen()" hidden$="[[!fullscreenAvailable]]">Display this page in full screen mode</button>

	<div id="errorDiv" hidden$="[[fullscreenAvailable]]">
		Your browser does not support the HTML5 full screen API... :(
	</div>
</template>

<script>
	function goFullscreen() {
	  var fsapi = document.querySelector('#fsapi');
	  fsapi.toggleFullscreen();
	}
</script>
```

* **fullscreen-icon-button**

```html
    <fullscreen-icon-button target="#myElementToDisplayFullscreen" title="fullscreen" alt="fullscreen" tabindex="0"></fullscreen-icon-button>
```

## Demo!

[Link](https://vguillou.github.io/webcomponents/fullscreen-api/demo/)

[Iframe demo](https://vguillou.github.io/webcomponents/fullscreen-api/demo/iframe.html)


## License

[MIT License](./LICENSE.md)
