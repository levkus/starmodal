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