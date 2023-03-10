<style>
p{
    font-family: Georgia;
    font-size: 30px;
}
.container {
  width: auto;
  display: flex;
  flex-direction: row;
}
.btn {
  margin: 20px auto;
  border: none;
  padding: 10px 44px;
  font-size: 36px;
  position: relative;
}
.btn::before {
  transition: all 0.85s cubic-bezier(0.68, -0.55, 0.265, 1.55);
  content: "";
  width: 50%;
  height: 100%;
  background: black;
  position: absolute;
  top: 0;
  left: 0;
}
.btn .btn-text {
  color: white;
  mix-blend-mode: difference;
}
.btn:hover::before {
  background: black;
  width: 100%;
}
.btn.rounded {
  border-radius: 50px;
}
.btn.rounded .text-green {
  color: #ffcc00;
  mix-blend-mode: difference;
}
.btn.rounded::before {
  border-radius: 50px;
  width: 25%;
  background: #ffcc00;
}
.btn.rounded:hover::before {
  background: #ffcc00;
  width: 100%;
}

#inp {
  position: relative;
  margin: auto;
  width: 100%;
  max-width: 280px;
  border-radius: 3px;
  overflow: hidden;
}
#inp .label {
  position: absolute;
  top: 20px;
  left: 12px;
  font-size: 16px;
  color: rgba(0, 0, 0, 0.5);
  font-weight: 500;
  transform-origin: 0 0;
  transform: translate3d(0, 0, 0);
  transition: all 0.2s ease;
  pointer-events: none;
}
#inp .focus-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.05);
  z-index: -1;
  transform: scaleX(0);
  transform-origin: left;
}
#inp input {
  -webkit-appearance: none;
  -moz-appearance: none;
       appearance: none;
  width: 100%;
  border: 0;
  font-family: inherit;
  padding: 16px 12px 0 12px;
  height: 56px;
  font-size: 16px;
  font-weight: 400;
  background: #696969;
  box-shadow: inset 0 -1px 0 #696969;
  color: white;
  transition: all 0.15s ease;
}
#inp input:hover {
  background: rgba(0, 0, 0, 0.04);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.5);
}
#inp input:not(:-moz-placeholder-shown) + .label {
  color: rgba(0, 0, 0, 0.5);
  transform: translate3d(0, -12px, 0) scale(0.75);
}
#inp input:not(:-ms-input-placeholder) + .label {
  color: rgba(0, 0, 0, 0.5);
  transform: translate3d(0, -12px, 0) scale(0.75);
}
#inp input:not(:placeholder-shown) + .label {
  color: rgba(0, 0, 0, 0.5);
  transform: translate3d(0, -12px, 0) scale(0.75);
}
#inp input:focus {
  background: rgba(0, 0, 0, 0.05);
  outline: none;
  box-shadow: inset 0 -2px 0 #0077FF;
}
#inp input:focus + .label {
  color: #0077FF;
  transform: translate3d(0, -12px, 0) scale(0.75);
}
#inp input:focus + .label + .focus-bg {
  transform: scaleX(1);
  transition: all 0.1s ease;
}
</style>
<script>
  // Is Leap Year
  function getYear(){
      let inputYear = document.getElementById("inputYear").value;
      return inputYear;
  }
  function isLeapYear(year) {
      result = document.getElementById("isLeapYearResult");
      // Fetch data from API
      fetch('http://spiderbiters.nighthawkcodingsociety.com/api/calendar/isLeapYear/' + year)
      .then(response => response.json())
      .then(data => {
          console.log(data);
          result.innerHTML = ": " + data.isLeapYear;
      })
  }

  //First Day of the year
  function getYear1(){
      let inputYear1 = document.getElementById("inputYear1").value;
      return inputYear1;
  }
  function firstDayOfYear(year1) {
      result = document.getElementById("firstDayOfYearResult");
      // Fetch data from API
      fetch('http://spiderbiters.nighthawkcodingsociety.com/api/calendar/firstDayOfYear/' + year1)
      .then(response => response.json())
      .then(data => {
          console.log(data);
          result.innerHTML = ": " + data.firstDayOfYear;
      })
  }

  //Day Of Week
  function getDate(){
      let inputDate = document.getElementById("inputDate").value;
      return inputDate;
  }
  function dayOfWeek(Date) {
      result = document.getElementById("dayOfWeekResult");
      // Fetch data from API
      fetch('http://spiderbiters.nighthawkcodingsociety.com/api/calendar/dayOfWeek/' + Date)
      .then(response => response.json())
      .then(data => {
          console.log(data);
          result.innerHTML = ": " + data.dayOfWeek;
      })
  }

  //Day Of Year
  function getDate1(){
      let inputDate1 = document.getElementById("inputDate1").value;
      return inputDate1;
  }
  function dayOfYear(Date1) {
      result = document.getElementById("dayOfYearResult");
      // Fetch data from API
      fetch('http://spiderbiters.nighthawkcodingsociety.com/api/calendar/dayOfYear/' + Date1)
      .then(response => response.json())
      .then(data => {
          console.log(data);
          result.innerHTML = ": " + data.dayOfYear;
      })
  }
</script>
<body>
 <!-- Is Leap Year -->
  <div class="container">
    <p>Is it a leap year?</p>
    <p id="isLeapYearResult"></p>
  </div>
  <div class="container">
    <label for="inp" id="inp">
      <input id="inputYear" class="inp">
      <span class="label">Year</span>
      <span class="focus-bg"></span>
    </label>
    <button onclick="isLeapYear(getYear())" class="btn rounded"><span class="text-green">Check</span></button>
  </div> 
  <hr>

<!-- First Day Of Year -->
  <div class="container">
    <p>What is the first Day of this Year?</p>
    <p id="firstDayOfYearResult"></p>
  </div>
  <div class="container">
    <label for="inp" id="inp">
      <input id="inputYear1" class="inp">
      <span class="label">Year</span>
      <span class="focus-bg"></span>
    </label>
    <button onclick="firstDayOfYear(getYear1())" class="btn rounded"><span class="text-green">Check</span></button>
  </div>
  <hr> 

  <!-- Day of Week -->
  <div class="container">
    <p>What is the day of the week for this date?</p>
    <p id="dayOfWeekResult"></p>
  </div>
  <div class="container">
    <label for="inp" id="inp">
      <input id="inputDate" class="inp">
      <span class="label">Month/Day/Year</span>
      <span class="focus-bg"></span>
    </label>
    <button onclick="dayOfWeek(getDate())" class="btn rounded"><span class="text-green">Check</span></button>
  </div> 
  <hr> 

  <!-- Day of Year -->
  <div class="container">
    <p>What is the day of the year for this date?</p>
    <p id="dayOfYearResult"></p>
  </div>
  <div class="container">
    <label for="inp" id="inp">
      <input id="inputDate1" class="inp">
      <span class="label">Month/Day/Year</span>
      <span class="focus-bg"></span>
    </label>
    <button onclick="dayOfYear(getDate1())" class="btn rounded"><span class="text-green">Check</span></button>
  </div> 
</body>