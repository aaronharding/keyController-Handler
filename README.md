# jQuery Continuous Key Press Handler

A jQuery based Javascript class that handles all key presses. Offers a continuous key press event on multiple keys at a custom refresh rate. Allows the setting of a different callback function for press and release of key.

## Requires

jQuery

## Defaults

<b>Continuous key press:</b> false

<b>Refresh rate:</b> 30 per second

## Usage

Instantiate the controller by assigning it to a variable. Good practice is to use the same variable name as the object. It is only neccesary to instantiate the KeyController object once. 

```javascript
var KeyController = new KeyController();
```

Assign functions to keys by calling the <b>add()</b> method from the handler. This method can be called multiple times for different keys.

```javascript
KeyController.add({
  key, // which key to assign following functions to
  down: function(){}, // function to run when key is pressed down, and the function that is run if continuous key press event is set
  up: function(){}, // function to run when key is released
  continuous, // boolean to toggle continuous key press. optional. default value: true
  rate // number of times per second to fire the down event whilst key is held down. optional. default value: 30
}); 
```

Pass the callback functions to the respective arguments. Assign them to a key. Toggle whether the <b>down()</b> function will run continuously, and if so, set the refresh rate.

In this example, the message "key has been pressed" will appear in the console 10 times a second whilst the user is holding down the "A" key. On release, the message "key has been released" will appear.

```javascript
KeyController.add({
  key: '65',
  down: function(){
    console.log('key has been pressed');
  },
  up: function(){
    console.log('key has been released');
  },
  continuous: true,
  rate: 10
}); 
```

## Full example

Below is a small example that continually prints a message in the console whilst the "A" key is pressed and held down, and then prints a last message when the "A" key has been released. Also it prints one message in the console when the "D" key is pressed, and then prints a message when the "D" key has been released.

```javascript

var KeyController = new KeyController();

KeyController.add({
  key: '65',
  down: function(){
    console.log('The A key has been pressed and this message will keep printing to the console at a rate of 10 per second.');
  },
  up: function(){
    console.log('The A key has been released, the messages will now stop.');
  },
  continuous: true,
  rate: 10
}); 

KeyController.add({
  key: '68',
  down: function(){
    console.log('The D key has been pressed.');
  },
  up: function(){
    console.log('The D key has been released.');
  },
  continuous: false
}); 
```
