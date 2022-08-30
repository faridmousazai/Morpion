<template>
  <div class="morpion" v-if="step==1">
    <h1 class="head">{{ msg }}</h1>
    <img src="https://media.gettyimages.com/photos/won-tic-rac-toe-game-picture-id559558279?s=612x612" alt="">
     <h2 class="head">Les Régles</h2>
    <ul class="head">
      <li>Jeu qui se joue à deux joueurs, sur un damier de 3 cases par 3 cases.</li>
      <li>Chaque joueur est représenté par un "symbole".</li>
      <li>Un joueur utilise toujours le même type de "symbole".</li>
      <li>Un premier joueur dessine son symbole sur une case. Puis c'est au tour de l'autre joueur de dessiner son symbole sur une case vide.</li>
      <li>Le but du jeu est de réussir à aligner ses trois symboles (horizontal, vertical ou diagonale), on remporte alors la partie.</li>
      <li>Si la grille est remplie et qu'aucune ligne ne comporte trois symboles identiques, les joueurs finissent par un match nul.</li>
    </ul> 
   <input  type="button" value="Let's go" @click="nextStep">
  </div>
  <div class="play" v-else-if="step==2"> <h3 class="head">Play!</h3>
  <p><span class="nought">NOUGHTS</span> & <span class="cross">CROSSES</span></p>
  <ul class="game">
            <li class="blank" id="a" @click="clickedOnCell($event, 1)"></li>
            <li class="blank" id="b" @click="clickedOnCell($event, 2)"></li>
            <li class="blank" id="c" @click="clickedOnCell($event, 3)"></li>
            <li class="blank" id="d" @click="clickedOnCell($event, 4)"></li>
            <li class="blank" id="e" @click="clickedOnCell($event, 5)"></li>
            <li class="blank" id="f" @click="clickedOnCell($event, 6)"></li>
            <li class="blank" id="g" @click="clickedOnCell($event, 7)"></li>
            <li class="blank" id="h" @click="clickedOnCell($event, 8)"></li>
            <li class="blank" id="i" @click="clickedOnCell($event, 9)"></li>
        </ul>
        <input type="button" value="Restart" @click="restart">
  </div>

</template>

<script>
export default {
  name: 'Morpion_game',
  props: {
    msg: String
  },
  data() {
    return {
      item: '',
      players: ['', '',''],
      playerPositions: [[], []],
      step:1,
      turn: 0
    }
    
  },
  methods: {
    nextStep() {
      this.step++
      
    },
   clickedOnCell(event, cellNumber) {

      if(event.target.className == "blank") {
        this.playerPositions[this.turn].push(cellNumber)
        if(this.turn==0){
          event.target.className = ' cross'
          this.turn = 1
        } else {
          event.target.className = ' nought'
          this.turn = 0
        }  
        this.checkIfSomeoneWon()
      }
    },

    
    checkIfSomeoneWon() {
      // this method is called each time a player clicks succesfully on a cell
      //console.log(this.playerPositions)
      //this.playerPositions contains two arrays
      // check if one of these arrays  contains a winning combination. If so, he won
      // if(a.cross == b.cross == c.cross){win},
      
      //let winningCombination = [ [1,2,3] , [4,5,6] ]
    },
    restart(){
      let liste_of_li = document.getElementsByTagName('li');
      for(let index in liste_of_li) {
        let li = liste_of_li[index]
        li.className = "blank"
      }
    },


  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.morpion{
  background-color: #080808;
}
.head{
  color: white;
  padding-top: 2rem;
}
h1{
   text-transform: uppercase;
  background-image: linear-gradient(
    -225deg,
    #6f59c0 0%,
    #8e58c7 29%,
    #ff1361 67%,
    #fff800 100%
  );
  background-size: auto auto;
  background-clip: border-box;
  background-size: 200% auto;
  color: #fff;
  background-clip: text;
  border-inline-color: transparent;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: textclip 3s linear infinite;
   
}

@keyframes textclip {
  to {
    background-position: 200% center;
  }
}


h2{
  margin-left: -80%;
  color: white;
}

.play{
  background: url("https://images.fineartamerica.com/images-medium-large-5/12-euglena-protozoa-marek-mis.jpg");
  height: 100vh;
  width: 100vw;
  background-size: cover;
}

ul {
  width: 50vw;
  color: white;
}

li {
   list-style-type:square; 
  line-height: 1.5em;
  text-align: left;
  
}
a {
  color: #42b983;
}
input{
  margin: 2rem;
  width: 10rem;
  height: 2rem;
  background-color: rgb(93, 86, 86);
  color:beige;
  border-radius: 16px;
  font-size: 20px;

}
input:hover{
  color: #9fd0ee;
  cursor: pointer;
  background-color: #236794;

}
ul.game {
    padding-top: 2rem;
    width: 365px;
    height: 350px;
    margin: 0 auto;
       display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 3px;
}

ul.game li {
    margin: 0;
    padding: 0;    
    background:#9fd0ee;
    display: inline-block;  
    cursor: pointer;
}
ul.game li:hover {
    background: rgb(79, 75, 75);
}

p {
    font-family: 'Oswald', sans-serif; 
    font-weight: 300;
    color: #666;
    text-align: center;
}



span.nought {
    color: #2a2d2f;
    background: #31b3eb;
    padding: 0px;
    font-size: 20px;
}

.cross {
    color: #42280f;
    background: #dea677;
    padding: 0px;
    font-size: 20px;
}

ul.game li.nought {
    background: url('https://st.depositphotos.com/1561359/4118/v/950/depositphotos_41184617-stock-illustration-3d-golden-letter-x.jpg') #A4DBF7 no-repeat;
    background-position: center center;
    background-size: 100% 100%;
}

ul.game li.cross {
    background: url('https://i.pinimg.com/originals/4c/f6/78/4cf6787902d19782326d328692a7915d.jpg') #f6724e no-repeat;
    background-position: center center;
    background-size: 100% 100%;
}

p.reset {
    text-align: center;
    color: #666;
    font-size: 20px;
    cursor: pointer;
}





/* Smartphones (portrait) ----------- */
@media only screen 
and (max-width : 450px) {

ul.game {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 300px;
    margin: 0 auto;
}

}
</style>
