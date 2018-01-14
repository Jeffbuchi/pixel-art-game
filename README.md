# pixel-art-game
The pixel art maker game is a web app that allows you to draw pixel art on a customizable canvas
The code goes here;
<!DOCTYPE html>
<html>
<head>
    <title>Pixel Art Maker!</title>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Monoton">
    <link rel="stylesheet" href="styles.css">	 
</head>
<body>
    <h1>Lab: Pixel Art Maker</h1>

    <h2>Choose Grid Size</h2>
    <form id="sizePicker">
        Grid Height:
        <input type="number" id="input_height" name="height" min="1" value="1">
        Grid Width:
        <input type="number" id="input_width" name="width" min="1" value="1">
        <input type="submit">
    </form>

    <h2>Pick A Color</h2>
    <input type="color" id="colorPicker">

    <h2>Design Canvas</h2>
    <table id="pixel_canvas">
  </table>

    <script src="designs.js"></script>
</body>
</html>


// Your code goes here!
	'use strict';
	const $colorPicker = document.getElementById("colorPicker");
	const $sizePicker  = document.getElementById("sizePicker");
	const $table = document.getElementById("pixel_canvas");
	
	// add listener to select grid size
	$sizePicker.addEventListener('submit', function() {
		// prevent page refresh on submit
		event.preventDefault();
		
		// get input data and draw grid
		let width = document.getElementById("input_width").value;
		let height = document.getElementById("input_height").value;
		makeGrid(width,height);
		

})

      // Draw grid
	  function makeGrid(width,height) {
		  $table.innerHTML = '';
		  for (let row = 0; row < width; row++) {
			  let newRow = $table.insertRow();
			  for (let cell = 0; cell <height; cell++) {
				  // add new cell with the listener to change color
				  let newCell = newRow.insertCell();
				  newCell.onclick = changeColor;
			  }
		  }
	  }
				  
      function changeColor() {
		  this.style.background = $colorPicker.value;
	  }
	  makeGrid();
