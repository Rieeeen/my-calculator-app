<script>
  //At first I use this 4 let so I can easily define the necesarry variables
  //So its more easy to control 
  let num1 = '';
  let num2 = '';
  let operator = '';
  let result = '';

  //The "display" variable will hold the calculators state and display value
  //This variable is initially set to an empty string so it will be updated whenever
  //there is a change in the calculators state
  let display = '';
  
  const updateDisplay = () => {
    display = `${num1} ${operator} ${num2} ${result}`;
  };

//-------------------------------------------
//This is the method that I use that can satisfy your condition without using  eval and function
//The HandleNumberClick handles the click event for number buttons from 0-9 
//It appends the clicked number to eiher num1 or num2 based on the current state of the operator
  const handleNumberClick = (event) => {
    const { target } = event;
    const number = target.innerText;

    if (!operator) {
      num1 += number;
    } else {
      num2 += number;
    }

    updateDisplay();
  };

  //handleOperatorClick handles the click event for operator buttons
  //It sets the operator variable to he clicked operator
  const handleOperatorClick = (event) => {
    const { target } = event;
    operator = target.innerText;

    updateDisplay();
  };

  //handleEqualClick handles the click event for the = button 
  //It performs the calculation based on the selected operator and update the result 
  const handleEqualClick = () => {
    if (operator === '+') {
      result = String(Number(num1) + Number(num2));
    } else if (operator === '-') {
      result = String(Number(num1) - Number(num2));
    } else if (operator === '*') {
      result = String(Number(num1) * Number(num2));
    } else if (operator === '/') {
      result = String(Number(num1) / Number(num2));
    }

    num1 = '';
    num2 = '';
    operator = '';

    updateDisplay();
  };

//handleClearClick handles the click event for clear the display by pressing C Button
  const handleClearClick = () => {
    num1 = '';
    num2 = '';
    operator = '';
    result = '';

    updateDisplay();
  };

  //handleBackspaceClick handles the click event for deleting 1 number by pressing DEL
  const handleBackspaceClick = () => {
    if (num2 !== '') {
      num2 = num2.slice(0, -1);
    } else if (operator !== '') {
      operator = '';
    } else if (num1 !== '') {
      num1 = num1.slice(0, -1);
    }

    updateDisplay();
  };

</script>