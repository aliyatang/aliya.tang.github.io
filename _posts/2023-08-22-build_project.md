---
toc: true
comments: true
layout: post
title: Build a Project
description: Continue learning the Development work flow for GitHub Pages index.md and _posts. Now is the time to build you first project.
type: hacks
courses: { csa: {week: 0} }
---
# Build a Project
Continue learning the Development work flow for GitHub Pages index.md and _posts. Now is the time to build you first project.

Conventional Calculator

<html>
<body>
<div class="calculator">
    <form>
        <input type="text" id="display" name="display" disabled>
        <div class="button-grid">
            <input type="button" id="num" value="7" onclick="appendCharacter('7')">
            <input type="button" id="num" value="8" onclick="appendCharacter('8')">
            <input type="button" id="num" value="9" onclick="appendCharacter('9')">
            <input type="button" id="opp" value="/" onclick="appendCharacter('/')" class="operator"> 
            <input type="button" id="num" value="4" onclick="appendCharacter('4')">
            <input type="button" id="num" value="5" onclick="appendCharacter('5')">
            <input type="button" id="num" value="6" onclick="appendCharacter('6')">
            <input type="button" id="opp" value="*" onclick="appendCharacter('*')" class="operator"> 
            <input type="button" id="num" value="1" onclick="appendCharacter('1')">
            <input type="button" id="num" value="2" onclick="appendCharacter('2')">
            <input type="button" id="num" value="3" onclick="appendCharacter('3')">
            <input type="button" id="opp" value="-" onclick="appendCharacter('-')" class="operator"> 
            <input type="button" id="num" value="0" onclick="appendCharacter('0')">
            <input type="button" id="equal" value="=" onclick="evaluateExpression()" class="equal operator">
            <input type="button" id="opp" value="." onclick="appendCharacter('.')" class="operator">
            <input type="button" id="opp" value="+" onclick="appendCharacter('+')" class="operator"> 
            <input type="button" id="opp" value="AC" onclick="clearDisplay()" class="operator">
            <input type="button" id="opp" value="DEL" onclick="deleteLastCharacter()" class="operator">
            <input type="button" id="opp" value="(" onclick="appendCharacter('(')" class="operator">
            <input type="button" id="opp" value=")" onclick="appendCharacter(')')" class="operator">
        </div>
    </form>
</div>
</body>
</html>

<style>
body {
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  background-color: #f0f0f0;
}

.calculator {
  background-color: #364757;
  border-radius: 10px;
  padding: 20px;
  text-align: center;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  width: 240px;
}

#display {
  width: 90%;
  padding: 10px;
  font-size: 20px;
  color: black;
  margin-bottom:20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.25);
  background-color: #9fb7cc;
}

.button-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 10px;
}

#num {
  width: 50px;
  height: 40px;
  font-size: 18px;
  background-color: #5c8cb8;
  border-color: #4174a3;
  color: white;
  border: 10;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

#opp {
  width: 50px;
  height: 40px;
  font-size: 18px;
  background-color: #414a75;
  border-color: #263266;
  color: white;
  border: 10;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

#equal {
  width: 50px;
  height: 40px;
  font-size: 18px;
  background-color: #68a392;
  border-color: #569180;
  color: white;
  border: 10;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}


</style>

<script>
const display = document.getElementById("display");
let isError = false;

function appendCharacter(character) {
  if (isError && !isNaN(character)) { // Clear display only when a NUM button is pressed
    display.value = "";
    isError = false;
  }

  display.value += character;
}

function clearDisplay() {
  display.value = "";
  isError = false;
}

function deleteLastCharacter() {
  display.value = display.value.toString().slice(0, -1);
}

function evaluateExpression() {
  try {
    display.value = eval(display.value);
    isError = false;
  } catch (error) {
    display.value = "Error";
    isError = true;
  }
}
</script>