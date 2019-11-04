//global

#define ROCK 91
#define PAPER 92
#define SCISSORS 93

#define B_ROCK 4
#define B_PAPER 5
#define B_SCISSORS 6

#define none 90

byte lastReadRock = 0;
byte lastReadPaper = 0;
byte lastReadScissors = 0;

long wins = 0;
long losses = 0;
long ties = 0;


void setup() { // week 1
  // put your setup code here, to run once:
  Serial.begin(9600);
  pinMode(B_ROCK, INPUT);
  pinMode(B_PAPER, INPUT);
  pinMode(B_SCISSORS, INPUT);
}

byte cpuPick(){
  return random(91,94);
}

byte listenToButtons(){ //week 1
  byte rock_read = digitalRead(B_ROCK);
  byte paper_read = digitalRead(B_PAPER);
  byte scissors_read = digitalRead(B_SCISSORS);
  byte ret = none;
  
  if(lastReadRock == HIGH && rock_read == LOW) ret = ROCK;
  if(lastReadPaper == HIGH && paper_read == LOW) ret = PAPER;
  if(lastReadScissors == HIGH && scissors_read == LOW) ret = SCISSORS;
  
  lastReadRock = rock_read;
  lastReadPaper = paper_read;
  lastReadScissors = scissors_read;
  delay(1);
  return ret;
}

byte playerPick(){ //week 2
  while (1){
  byte ret = listenToButtons();
  if (ret != none)return ret;
  }
  
}

void playGame(){
  byte player = playerPick();
  byte cpu = cpuPick();
  evaluatePicks(player, cpu);
  report(player, cpu);
}

void evaluatePicks(byte player, byte cpu){ // week 2
  if (player == cpu) tie();
  if (player == ROCK && cpu == SCISSORS || player == PAPER && cpu == ROCK || player == SCISSORS && cpu == PAPER) win();
  if (cpu == ROCK && player == SCISSORS || cpu == PAPER && player == ROCK || cpu == SCISSORS && player == PAPER) lose();
}


//week 2
void win(){
  Serial.println("Win");
  wins ++;
}

void lose(){
  losses ++;
  Serial.println("Lose");
}

void tie(){
  Serial.println("Tie");
  ties ++;
}

// week 2+
String translatePick(byte number){
  String ret = "";
  if (number == ROCK) return "ROCK";
  if (number == PAPER) return "PAPER";
  if (number == SCISSORS) return "SCISSORS";
}

// week 2+
void report(byte player, byte cpu){
  String message = "Player has " + String(wins) + " wins " + ", " + String(losses) + " losses " + " and " + String(ties) + " ties";  
  Serial.println(message);
  message = "Player picked " + translatePick(player) + ". CPU picked " + translatePick(cpu) + ".";
  Serial.println(message);
}

// week 2+
void bling(){

  
}

void loop() {
  playGame();
  Serial.println("loop call");
}
