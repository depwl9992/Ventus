Ventus WM
===========================

A window manager experiment written in Javascript, HTML5 and CSS3.

<a href="http://www.rlamana.es/ventus">Live Demo!</a> (http://www.rlamana.es/ventus) | <a href="https://vimeo.com/62041866">Video Demo</a>

### Create a new window manager

	var wm = new Ventus.WindowManager();
	
### Create a new empty window

	var window = wm.createWindow({
		title: 'A new window',
		x: 50,
		y: 50,
		width: 400,
		height: 250
	});
	
	window.open();
	
### Create a new window wrapping a DOM Element

##### Using a query
	wm.createWindow.fromQuery('#element .selector', {
		title: 'My App',
		width: 330,
		height: 400,
		x: 670,
		y: 60
	});
	
##### Using a reference
	wm.createWindow.fromElement(domElement, {
		title: 'My App',
		width: 500,
		height: 500,
		x: 0,
		y: 0
	});

### Listen to events

#### Define handlers in constructor
	var window = wm.createWindow({
		title: 'A new window',
		events: {
			open: function() {
				console.log('The window was open');
			},
			
			closed: function() {
				console.log('The window was closed');
			},
		}
	});

#### Using the 'signals' property
	var window = wm.createWindow({
		title: 'A new window'
	});
	
	window.signals.on('open', function() {
		console.log('The window was open');
	});
	
### Destroying a window
When a window is closed the content is not destroyed by default. This way windows can be open again keeping the wrapped DOM element. To completely destroy the window, the method 'destroy' needs to be called:

	var window = wm.createWindow({
		title: 'A new window',
		events: {
			closed: function() {
				this.destroy();
			}
		}
	});
