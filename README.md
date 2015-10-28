# &lt;fullscreen-api&gt;

_A simple Polymer based Web Component wrapper for the HTML5 full screen API._

Please refer to the <a href="https://vguillou.github.io/webcomponents/fullscreen-api/">component page</a> for more informations.

This Polymer Web-Component lets you define which element to display in full screen mode
(via the 'target' attribute) and toggle normal/full screen
mode by calling the 'toggleFullscreen()' method.
Note that this method MUST be triggered directly by user interaction
(typically in a native 'onclick' or Polymer's 'on-click' handler).
If no 'target' is set, the whole page (more specifically
'document.documentElement') while be displayed full screen.

### Attributes

* **target** :
The element to display full screen (document.documentElement by default).
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

## Demo!

[Link](https://vguillou.github.io/webcomponents/fullscreen-api/demo.html)

[Iframe demo](https://vguillou.github.io/webcomponents/fullscreen-api/demo_iframe.html)


## License

[MIT License](http://opensource.org/licenses/MIT)
