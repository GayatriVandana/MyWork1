# MyWork1
<!DOCTYPE html>
<html>
<head>
	<title>Clock Example</title>
</head>

<style type="text/css">
video {
	min-height: 100%;
	min-width: 100%;
	
}

</style>

<body>
	<div style="position:absolute; top:50px; left:450px; z-index:1"> 
		<canvas id="canvas" width="500" height="500"></canvas>
	</div>

	<video id="myvideo" class="video" loop>
		<source src="Images/demo.mp4" type="video/mp4">
	</video>

<script type="text/javascript">
	var canvas = document.getElementById("canvas");
	var context = canvas.getContext("2d");

	

	context.strokeStyle = "#89E894";
	context.lineCap = "round";
	context.lineWidth = "15";
	context.shadowBlur = "#89E894";
	context.shadowWidth = "15";

	function degreetoRadian(degree) {
	var factor = Math.PI/180;
	return degree*factor;
	}

	function showTime() {
	var presentDate = new Date();
	// console.log(presentDate);
	var readableDate = presentDate.toDateString();
	var readableTime = presentDate.toLocaleTimeString();
	// console.log(readableTime);
	var hours = presentDate.getHours();
	if(hours>12){
		hours = hours-12;
	}
	var minutes = presentDate.getMinutes();
	var seconds = presentDate.getSeconds();
	var milliseconds = presentDate.getMilliseconds();
	var newSeconds = seconds + (milliseconds/1000);

	var background = context.createRadialGradient(250, 250, 5, 250, 250, 300);
	background.addColorStop(0, "#09303a");
	background.addColorStop(1, "#000000");
	context.fillStyle = background;
	context.fillRect(0, 0, 500, 500);

	context.beginPath();
	context.arc(250, 250, 200, degreetoRadian(270), degreetoRadian((hours*30)-90));
	context.stroke();

	context.beginPath();
	context.arc(250, 250, 170, degreetoRadian(270), degreetoRadian((minutes*6)-90));
	context.stroke();

	context.beginPath();
	context.arc(250, 250, 140, degreetoRadian(270), degreetoRadian((newSeconds*6)-90));
	context.stroke();

	context.font = "16px Arial";
	context.fillStyle = "#89E894";
	context.fillText(readableDate, 200, 250);

	context.font = "16px Arial";
	context.fillStyle = "#89E894";
	context.fillText(readableTime, 200, 280);
	

	}
	setInterval (showTime, 40);

	(function() {
			var videos = document.getElementById("myvideo");
			videos.addEventListener ("canplay", function(){
			videos.play();
			});
		})();
</script>

</body>
</html>
