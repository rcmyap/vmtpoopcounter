<!DOCTYPE html>
<html ng-app="myApp">
<head>
<link rel="stylesheet" href = "https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
<script src= "https://ajax.googleapis.com/ajax/libs/angularjs/1.3.0/angular.min.js"></script>
<script src="https://cdn.firebase.com/js/client/2.0.4/firebase.js"></script>
<script src="https://cdn.firebase.com/libs/angularfire/0.8.0/angularfire.min.js"></script>
<!-- Anagular-char data -->
<link rel="stylesheet" href=
"https://cdn.rawgit.com/jtblin/angular-chart.js/master/dist/angular-chart.css" type=
"text/css" />
<script src="https://cdn.rawgit.com/nnnick/Chart.js/master/Chart.min.js" type=
"text/javascript">
</script>
<script src=
"https://cdn.rawgit.com/jtblin/angular-chart.js/master/dist/angular-chart.js"
type="text/javascript">
</script>
<!-- Setting the size of the charts -->
<style>
.chart {
width: 500px;
height: 500px;
}
</style>
</head>
<body ng-controller="userController" >
<div class="container">
<img src="http://cdn.shopify.com/s/files/1/0150/5180/products/Poop_1024x1024.jpg?v=1415395151" height="60%" width="60%" />
<h3> Shit Counter </h3>
Quick and dirty. <br><br>
<button class="btn btn-success" ng-click="addCounter(theKey)">
Add Counter
</button> with the key <input ng-model="theKey" type="input" ng-init="theKey='awesome'">
<br>
Counters: <br>
<table cellpadding="10">
<tr>
<th>Counter</th>
<th>Count</th>
</tr>
<tr ng-repeat="(k,v) in counters">
<td style="text-align:center">{{k}}</td>
<td style="text-align:center">{{v}}</td>
<td>
<button class="btn btn-success" ng-click="incrementCounter(k)">
<span class="glyphicon"></span> Increment
</button>
<button class="btn btn-success" ng-click="addCounter(k)">
<span class="glyphicon"></span> Reset
</button>
<button class="btn btn-success" ng-click="deleteCounter(k)">
<span class="glyphicon"></span> Delete
</button>
</td>
</tr>
</table>
<br>
<br>
<br>
</div> <!-- container -->
<script>
var myApp = angular.module("myApp", ["firebase","chart.js"]);
myApp.controller('userController', ['$scope', '$firebase',
function($scope, $firebase) {
$scope.newuser = {};
// Here is where you update your Firebase URL.
var theFirebaseURL = "https://vmtpoopcount.firebaseio.com";
var ref = new Firebase(theFirebaseURL);
//Counters and timers development
$scope.counters = $firebase(ref.child("counters")).$asObject();
$scope.timers = $firebase(ref.child("timers")).$asObject();
$scope.server = $firebase(ref.child("server")).$asObject();
$scope.queues = $firebase(ref.child("queues")).$asObject();
//Sometime it is easier to work with data as an array.
$scope.theCounters = $firebase(ref.child("counters")).$asArray();
$scope.updateCurrentTime = function() {
ref.child("server").transaction(function(currentValue) {
return {'currentTime': Firebase.ServerValue.TIMESTAMP}
});
};
$scope.updateCurrentTime();
$scope.timerCount = 0;
$scope.localIntervals = {};
//Start a maxCount interval and add it to the interval tracking list.
$scope.updateUntilCounter = function() {
maxCount = $scope.intervalCounter.target;
counterKey = $scope.intervalCounter.name;
interval = $scope.intervalCounter.interval;
var intervalToStop = setInterval(function () {myCounterTimer( counterKey,maxCount,intervalToStop)}, interval);
//Add to local object for tracking.
var temp = {'counterKey':counterKey,'maxCount':maxCount,'interval':interval}
$scope.localIntervals[intervalToStop] = temp;
}
//If the maxCount has been reached, stop the interval
function myCounterTimer(counterName, maxCounter, intervalToStop) {
//You could automatically update the chart as you are locally incrementing counters.
//$scope.update_the_chart();
if($scope.counters[counterName]<maxCounter){
console.log("updating counter "+counterName+" from "+$scope.counters[counterName]);
$scope.incrementCounter(counterName);
}
else { $scope.stopInterval(intervalToStop);}
};
//Start an update until counter expires interval
$scope.updateCounterUntilTimerExpires = function(){
timer = $scope.intervalCounter.timer;
counterKey = $scope.intervalCounter.name;
interval = $scope.intervalCounter.interval;
var intervalToStop = setInterval(function () {myCounterTimeoutTimer( counterKey,timer,intervalToStop)}, interval);
var temp = {'counterKey':counterKey,'timer':timer,'interval':interval}
$scope.localIntervals[intervalToStop] = temp;
}
//If the timer has expired, then stop the interval.
function myCounterTimeoutTimer(counterName, timer, intervalToStop) {
//update current server time.
$scope.updateCurrentTime();
//Determine of the timer has expired.
var timeToGo = $scope.timers[timer].duration - ($scope.server.currentTime - $scope.timers[timer].start);
if(timeToGo > 0 ){
console.log("updating counter "+counterName+" from "+$scope.counters[counterName] +" time to go "+timeToGo);
$scope.incrementCounter(counterName);
}
else { $scope.stopInterval(intervalToStop); }
}
$scope.stopInterval = function(intervalToStop){
console.log("stopping counter timer.");
clearInterval(intervalToStop);
delete $scope.localIntervals[intervalToStop];
$scope.$digest(); //In case the GUI does not update.
};
$scope.addCounter = function(counterName) {
ref.child("counters/"+counterName).transaction(function(currentValue) {
return 0;
});
};
$scope.incrementCounter = function(counterName) {
ref.child("counters/"+counterName).transaction(function(currentValue) {
return currentValue+1;
});
};
$scope.deleteCounter = function(counterName) {
console.log("deleting");
ref.child("counters/"+counterName).remove();
};
$scope.addTimer = function(timerName,duration) {
ref.child("timers/"+timerName).transaction(function(currentValue) {
return {'start': Firebase.ServerValue.TIMESTAMP, 'duration':duration};
});
$scope.updateCurrentTime();
};
$scope.resetTimer = function(timerName) {
ref.child("timers/"+timerName).transaction(function(currentValue) {
return {'start': Firebase.ServerValue.TIMESTAMP,'duration':currentValue.duration};
});
// need to pass duration.
$scope.updateCurrentTime();
};
$scope.deleteTimer = function(timerName) {
console.log("deleting");
ref.child("timers/"+timerName).remove();
$scope.updateCurrentTime();
};
$scope.addTask = function(queueName, counterName){
var task = {'task':'Update Counter','data':counterName};
theQueue = $firebase(ref.child("queues").child(queueName)).$asArray();
theQueue.$add(task);
};
$scope.deleteQueue = function(queueName) {
ref.child("queues/"+queueName).remove();
};
$scope.processTask = function(queueName,taskName) {
//execute the task here before deleteing.
//Do something with this task.
if($scope.queues[queueName][taskName].task=="Update Counter"){
$scope.incrementCounter($scope.queues[queueName][taskName].data)
ref.child("queues/"+queueName+"/"+taskName).remove();
} else {
console.log("Checking the empty queue "+queueName);
}
};
$scope.processTasksUntilCounter = function(counterKey,maxCount,queue,interval){
console.log("here");
var intervalToStop = setInterval(function () {myProcessingTimer( counterKey,maxCount,queue,intervalToStop)}, interval);
//Add to local object for tracking.
var temp = {'counterKey':counterKey,'maxCount':maxCount,'interval':interval}
$scope.localIntervals[intervalToStop] = temp;
}
//If the maxCount has been reached, stop the interval
function myProcessingTimer(counterName, maxCounter, queueName,intervalToStop) {
if($scope.counters[counterName]<maxCounter){
console.log("Todo: Processing task in queue"+queueName+" while counter "+counterName);
//$scope.theQueue = $firebase(ref.child("queues").child(queueName)).$asArray();
$scope.incrementCounter(counterName);
//Find task name of task 0 if any in the queue.
if ( (queueName in $scope.queues) && Object.keys($scope.queues[queueName]).length >0){
console.log(Object.keys($scope.queues[queueName]));
$scope.processTask(queueName,Object.keys($scope.queues[queueName])[0]);
//Update the counter.
}else{
//If there are no more tasks.
//$scope.stopInterval(intervalToStop);
}
}
else {
//If counter has exceeded limit.
$scope.stopInterval(intervalToStop);
}
};
// angular-charts starter data shown before first click.
//$scope.labels = ["Click", "to", "Update","Counters", "!"];
//$scope.series = ['Counters', 'Queue Lengths'];
//$scope.data = [
// [10,20,30,40,35],
// [15,5,25,30,25]
// ];
$scope.update_the_chart = function(){
console.log("Updating the chart.");
$scope.labels = [];
$scope.myCounters = [];
$scope.data = [$scope.myCounters];
//you can have multiple lines or bars for each X value.
//$scope.data = [$scope.myCounters, $scope.myCounters];
for(var i=0, len = $scope.theCounters.length; i < len; i++) {
$scope.labels.push($scope.theCounters[i].$id);
$scope.data[0].push($scope.theCounters[i].$value);
}
};
$scope.onClick = function (points, evt) {
$scope.update_the_chart();
};
$scope.counters.$loaded().then(function() {
$scope.update_the_chart();
});
var unwatch_counters = $scope.counters.$watch(function() {
console.log("counter data changed!");
$scope.update_the_chart();
});
//unwatch_counters();
}]); //close the controller and module.
</script>
<!-- Google Tracking code. Change the UA-XXXXXXX key to be yours -->
<script>
(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
})(window,document,'script','//www.google-analytics.com/analytics.js','ga');
ga('create', 'UA-32403946-2', 'auto');
ga('send', 'pageview');
</script>
</body>
</html>
