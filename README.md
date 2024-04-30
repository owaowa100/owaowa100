- 👋 Hi, I’m @owaowa100

<div class="countup" id="countup1">
  <span class="timeel years">00</span>
  <span class="timeel timeRefYears">years</span>
  <span class="timeel days">243</span>
  <span class="timeel timeRefDays">days</span>
  <span class="timeel hours">21</span>
  <span class="timeel timeRefHours">hours</span>
  <span class="timeel minutes">07</span>
  <span class="timeel timeRefMinutes">minutes</span>
  <span class="timeel seconds">00</span>
  <span class="timeel timeRefSeconds">seconds</span>
</div>
window.onload = function() {
  // Month Day, Year Hour:Minute:Second, id-of-element-container
  countUpFromTime("aug 30, 2023 21:07:00", 'countup1'); // ****** Change this line!
};
function countUpFromTime(countFrom, id) {
  countFrom = new Date(countFrom).getTime();
  var now = new Date(),
      countFrom = new Date(countFrom),
      timeDifference = (now - countFrom);
    
  var secondsInADay = 60 * 60 * 1000 * 24,
      secondsInAHour = 60 * 60 * 1000;
    
  days = Math.floor(timeDifference / (secondsInADay) * 1);
  years = Math.floor(days / 365);
  if (years > 1){ days = days - (years * 365) }
  hours = Math.floor((timeDifference % (secondsInADay)) / (secondsInAHour) * 1);
  mins = Math.floor(((timeDifference % (secondsInADay)) % (secondsInAHour)) / (60 * 1000) * 1);
  secs = Math.floor((((timeDifference % (secondsInADay)) % (secondsInAHour)) % (60 * 1000)) / 1000 * 1);

  var idEl = document.getElementById(id);
  idEl.getElementsByClassName('years')[0].innerHTML = years;
  idEl.getElementsByClassName('days')[0].innerHTML = days;
  idEl.getElementsByClassName('hours')[0].innerHTML = hours;
  idEl.getElementsByClassName('minutes')[0].innerHTML = mins;
  idEl.getElementsByClassName('seconds')[0].innerHTML = secs;

  clearTimeout(countUpFromTime.interval);
  countUpFromTime.interval = setTimeout(function(){ countUpFromTime(countFrom, id); }, 1000);
}
