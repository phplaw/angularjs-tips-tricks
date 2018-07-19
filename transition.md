```css
/**
 * Move in a circle without wrapper elements
 * Idea by Aryeh Gregor, simplified by Lea Verou
 */

@keyframes rot {
	from {
		transform: rotate(0deg)
		           translate(-150px)
		           rotate(0deg);
	}
	to {
		transform: rotate(360deg)
		           translate(-150px) 
		           rotate(-360deg);
	}
}

.smile {
	width: 40px;
	height: 40px;
	position: absolute;
	top: 200px;
	left: 50%;
	margin: -20px;
	font-size: 100px;
	animation: rot 3s infinite linear;
}
/* html code: <div class="smile">☺</div> */
```



http://svgjs.com/elements/
https://greensock.com/docs/Easing/SlowMo
https://www.kirupa.com/html5/animating_movement_smoothly_using_css.htm

http://tobiasahlin.com/blog/curved-path-animations-in-css/

https://www.w3schools.com/howto/howto_css_loader.asp

http://tobiasahlin.com/blog/curved-path-animations-in-css/ [good one]

http://jsfiddle.net/W69s6/20/
http://jsfiddle.net/Cu6Zv/1/
