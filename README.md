# &lt;fullscreen-api&gt;

_A simple Polymer based Web Component wrapper for the HTML5 full screen API._

It lets you define which element to display in full screen mode
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

## Example 1

```html
<fullscreen-api id="fsapi"></fullscreen-api>

<button type="button" onclick="goFullscreen()">Display this page in full screen mode</button>

<script>
window.addEventListener('polymer-ready', function() {
    var fsapi = document.querySelector('#fsapi');
    if (!fsapi.fullscreenAvailable) {
      document.body.innerHTML = 'Your browser does not support the HTML5 full screen API... :(';
    }
  });

function goFullscreen() {
  var fsapi = document.querySelector('#fsapi');
  fsapi.toggleFullscreen();
}
</script>
```

## Example 2 (with data-binding, inside a Polymer template)

```html
<style>
	img {
	  width: 300px;
	  height: 200px;
	}

	img:-webkit-full-screen {
	  width: 100%;
	  height: auto;
	}
	img:-moz-full-screen {
	  width: 100%;
	  height: auto;
	}
	img:-ms-fullscreen {
	  width: 100%;
	  height: auto;
	}
	img:full-screen {
	  width: 100%;
	  height: auto;
	}
	img:fullscreen {
	  width: 100%;
	  height: auto;
	}
</style>

<fullscreen-api id="fsapi" target="{{$.photo}}"></fullscreen-api>

<img id="photo" src="my_photo.jpg" on-click="{{goFullscreen}}" alt="My Photo"></img>

<script>
Polymer({
	...
	goFullscreen: function() {
		this.$.fsapi.toggleFullscreen();
	}
	...
});
</script>
```

## Demo!

[Link](https://vguillou.github.io/webcomponents/fullscreen-api/demo.html)

[Iframe demo](https://vguillou.github.io/webcomponents/fullscreen-api/demo_iframe.html)


## License

[MIT License](http://opensource.org/licenses/MIT)
