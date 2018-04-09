# StarModal
A simple Modal ES6 module with no dependencies.

## Setup
### In your HTML:
````html
<div style="display: none">
  <div id="some-content">
    Your content goes here
  </div>
</div>
````

### In your JavaScript:
````javascript
import StarModal from './starmodal'

// create StarModal instance
const modal = new StarModal()

// Create config object. All settings in config object are optional.
const config = {
  classNames: {
    overlay: 'your-overlay-class', // default: 'starmodal-overlay'
    modalBody: 'your-modal-body-class', // default: 'starmodal-body'
    modalContent: 'your-modal-content-class', // default: 'starmodal-content'
    closeButton: 'your-close-button-class', // default: 'starmodal-close-button'
  },
  closeButton: {
    text: 'Your text', // default: '' 
    parent: 'overlay', // sets if close button should be attached to overlay or modal itself. default: 'modal'
    innerHTML: '<i class="fa fa-times"></i>', // sets innerHTML of close button, overwrites text property. default: undefined
  },
  transitionClassNames: {
    overlayIn: 'your-overlay-in-class', // default: 'starmodal-overlay-in'
    overlayOut: 'your-overlay-out-class', // default: 'starmodal-overlay-out'
    modalIn: 'your-modal-in-class', // default: 'starmodal-modal-in'
    modalOut: 'your-modal-out-class', // default: 'starmodal-modal-out'
  }
}

// Initialize StarModal
modal.init({ ...config })

// Grab your content
const content = document.getElementById('some-content')

// Put your content inside modal. StarModal makes a clone of your
// content node and deletes it after it closes.
modal.show(content)
````

### default CSS:
````css
.starmodal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow-y: auto;
  box-sizing: border-box;
  padding: 40px;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
}

.starmodal-body {
  position: relative;
  box-sizing: border-box;
  margin: auto;
  padding: 40px;
  background: #fff;
}

.starmodal-content {
  box-sizing: border-box;
  min-width: 600px;
}

.starmodal-close-button {
  position: absolute;
  top: 20px;
  right: 20px;
  overflow: hidden;
  box-sizing: border-box;
  padding: 0;
  width: 40px;
  height: 40px;
  border: none;
  background: transparent;
  line-height: 40px;
  cursor: pointer;
  transition: color 0.3s;
}

.starmodal-close-button:hover {
  color: red;
}

.starmodal-close-button:before {
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  width: 100%;
  height: 100%;
  content: '+';
  text-align: center;
  font-size: 40px;
  line-height: 0.9;
  transform: rotate(45deg);
  transform-origin: center;
}

.starmodal-overlay-out {
  opacity: 0;
  transition: 0.2s;
}

.starmodal-overlay-in {
  opacity: 1;
  transition: 0.5s;
}

.starmodal-modal-out {
  transition: 0.2s;
  transform: translateY(-100px);
}

.starmodal-modal-in {
  transition: 0.5s;
  transform: translateY(0);
}
````