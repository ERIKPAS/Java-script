# Java-script
let userScore = 0;
let computerScore = 0;
const userScore_span = document.getElementById("user-score");
const computerScore_span = document.getElementById("computer-score");
const scoreBoard_div = document.querySelector(".Score");
const result_div = document.querySelector(".result > p");
const rock_div = document.getElementById("rock-choice");
const scissor_div = document.getElementById("scissors-choice");
const paper_div = document.getElementById("paper-choice");

function getComputerChoice() {
	const choices = ['rock-choice', 'paper-choice', 'scissors-choice'];
	const randomNumber = (Math.floor(Math.random() * 3));
	return choices[randomNumber]; 
}

function convertToWord (word) {
	if (word === "rock-choice") return "The Rock"
	if (word === "scissors-choice") return "Nožnice"
	return "Papier"
}

function win(userChoice , computerChoice) {
	userScore++;
	userScore_span.innerHTML = userScore;
	result_div.innerHTML = convertToWord(userChoice) + " porazí " + convertToWord(computerChoice)
}
function lose (userChoice, computerChoice) {
	computerScore++;
	computerScore_span.innerHTML = computerScore;
	result_div.innerHTML = convertToWord(computerChoice) + " porazí " + convertToWord(userChoice)
	
}
function draw (computerChoice) {
	computerScore = computerScore;
	computerScore_span.innerHTML = computerScore;
	result_div.innerHTML = "Je to remíza!"
	
}

function game(userChoice) {
	const computerChoice = getComputerChoice();
	switch (userChoice + computerChoice) {
		case "rock-choicescissors-choice":
		case "paper-choicerock-choice":
		case "scissors-choicepaper-choice": 
			win(userChoice , computerChoice );
			break;
		case "paper-choicescissors-choice":
		case "scissors-choicerock-choice":
		case "rock-choicepaper-choice": 
			lose(userChoice , computerChoice);
			break;
		case "paper-choicepaper-choice":
		case "scissors-choicescissors-choice":
		case "rock-choicerock-choice": 
			draw(userChoice , computerChoice); 
			break;
	}
}

function main() {
	rock_div.addEventListener('click', function() {
		game("rock-choice") ;
	} )
	scissor_div.addEventListener('click', function() {
		game("scissors-choice");
	} )
	paper_div.addEventListener('click', function() {
		game("paper-choice");
	} )
}

main();
