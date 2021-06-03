<template>
  <div id="app">
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.10.1/css/all.css">
    <div class="music_container">
     <header id="title" class="glow"><b>MY MUSIC</b></header>
      <div class="img_container " >
        
        <img class="main-img " id="anime" src="./assets/Picture/chris.gif">     </div>
     
     <main>
       <section class="player">
         <h2 class="song-title"> {{current.title}}<span class="artist">{{current.artist}}</span></h2><br><br><br>
         
         <div class="music_controls">
           <i class="fas fa-backward" id="prev" title="Previous" @click="prev"></i> 
            <i class="fas fa-play main_button" id="play" title="Play"  v-if="!isPlaying" @click="play"></i>
            <i class="fas fa-pause main_button" id="pause" title="Pause"  v-else @click="pause"></i>
             <i class="fas fa-forward" id="next" title="Next" @click="next"></i>

         <!--  <button class="prev" @click="prev">Prev</button>
           <button class="play"  v-if="!isPlaying" @click="play">Play</button>
           <button class="pause" v-else @click="pause">Pause</button>
           <button class="next" @click="next">Next</button>
         --></div>
       </section>
       <section class="playlist">
         <div class="dropdown"><span> Next In Queue</span>
         <div class="dropdown_content">
          <img class="pht omkimg" src='./assets/Picture/ask.jpg' alt="">
          <img  class="pht madimg" src='./assets/Picture/madhavan.jpeg' alt="">
          <img  class="pht myimg" src="https://mysonglyrics.net/wp-content/uploads/2020/03/Marappadhilai-Nenje-Song-Lyrics-Oh-My-Kadavule.jpg" alt="">
          <img  class="pht masimg" src='./assets/Picture/Master.jpg' alt="">
          <img class="pht bgimg" src="https://www.cinemahashtag.com/wp-content/uploads/2020/07/maxresdefault-4.jpg" alt="" >   
  <img class="pht remoimg" src="./assets/Picture/remo.jpg" alt="">
  <img  class="pht tamimg" src="./assets/Picture/tamilselvi.jpg" alt="">
<img class="pht sinimg" src="./assets/Picture/singapenne.jpg" alt="">
<img class="pht komimg" src="./assets/Picture/komali.jpg" alt="">
  <span>
        <button id="song-list" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
           {{song.title}} <span class="artist">{{song.artist}}</span>
       </button>
         </span>
        
         </div>
         
       </div>
        
       </section>
     </main>
     </div>
  </div>
</template>

<script>

export default {
  name: 'App',

  data(){
    return{
      current:{},
      index: 0,
      isPlaying: false,
      songs: [
      {
             title:'Kadhaipoma',
             src: require('./assets/Songs/kadhaipomma.mp3'),
             artist:'Oh My Kadavule -Leon James and Sid Sriram ',
            
         },
         {
          title:'Nenjai Poopole',
          src: require('./assets/Songs/poopole.mp3'),
          artist:'Minnalae - Harish Raghavan',
                   
        },
        {
          title:'Marapadhilai Nenje',
          src: require('./assets/Songs/Marappadhilai Nenje.mp3'),
          artist:'Oh My Kadavule - Sid Sriram',
            
        },
        {
          title:'Kutty Story',
          src: require('./assets/Songs/kutty story.mp3'),
          artist:'Master - Aniruth Ravichandhran',
           
        },
        {
          title:'Chellama',
          src: require('./assets/Songs/Chellamma.mp3'),
          artist:'Doctor - Aniruth Ravichandhran',
          

        },
        {
          title:'Senjitalay',
          src: require('./assets/Songs/Senjitaley.mp3'),
          artist:'Doctor - Aniruth Ravichandhran',
          

        },
        {
          title:'Vaa di yen Tamilselvi',
          src: require('./assets/Songs/Vaa di yen Tamilselvi.mp3'),
          artist:'Remo - Aniruth Ravichandhran',
          

        },
                
        {
          title:'Paisa note',
          src: require('./assets/Songs/Paisa Note.mp3'),
          artist:'Komali - Aniruth Ravichandhran',
          

        },
        {
          title:'Verithanam',
          src: require('./assets/Songs/Verithanam.mp3'),
          artist:'Master - AR.rahuman'
          

        }
      ],
      player: new Audio(),
  
    }
  },
 
  methods:{
       play(song){
         
          if(typeof song.src != "undefined"){
            this.current = song;
            this.player.src = this.current.src;
          
          }
          
          this.player.play();
          this.isPlaying = true;
          
       },
       pause(){
         this.player.pause();
         this.isPlaying = false;
       },
       next(){
         this.index++;
         if(this.index > this.songs.length - 1){
           this.index = 0;
         }

         this.current = this.songs[this.index];
         this.play(this.current);
       },
       prev() {
         this.index--;
         if(this.index < 0 ){
           this.index = this.songs.length - 1;
         }

         this.current = this.songs[this.index];
         this.play(this.current);
       }

},
  created(){
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Philosopher:ital@1&display=swap');
*,
*::before,
*::after {
  margin:0;
  padding:0;
  box-sizing:border-box;

}
body{
  font-family:'Philosopher', sans-serif;
  
}
#title
{
  display: flex;
  justify-content: center;
  align-items:center;
  margin-top: -5rem;
  color:rgb(241, 18, 55);
  margin:auto;
  
}
.song-title{
  margin:auto;
  color:white;
  margin-bottom:2rem;
  margin-top:-2rem;
 
}
#app{
  width: 100vw;
  height: 100vh;
  display:grid;
  place-items: center;
  
  animation-delay:0s;

}
.music_container {
  width: 35rem;
  height: 105rem;
  background-color:black;
  border-radius: 2rem;
  box-shadow: 0 1.2rem 3rem 0.5rem rgba(0, 0, 0, 0.2);
  padding:3rem;
  
  text-align:center;
  }
  .music_container  #title{
    text-transform: uppercase;
    word-spacing: 0.5rem;
    color:white;
    margin: 2rem 0 0.5rem 0;
    font-size: 2.5rem;
    font-weight:500;
    font-family:helvetica;
    padding-bottom:1.5rem;
    margin-top:1.5rem;
    text-shadow: 0 0.3rem 0.5rem rgba(0, 0, 0, 0.3);
  }
  .music_container #artist{
    color:#cccaca;
    text-transform: capitalize;
    letter-spacing: 0.1rem;
    font-size: 2rem;
    margin-bottom: 4rem;
    font-weight: 300;
  }
  .img_container{
    width:25rem;
    height:25rem;
    margin: auto;
    margin-bottom:-5rem;
  }
  
  .music_controls {
    width: 20rem;
    display: flex;
    justify-content: space-between ;
    margin: auto;
    align-items:center;
    margin-top: -3rem;
  }
  .music_controls .fas{
   
    color: #fff;
    font-size:1rem;
    cursor:pointer;
    filter: drop-shadow(1.2rem 3rem 0.55rem rgba(0, 0, 0, 0.4));

  }
  .music_controls .main_button {
    width: 4rem;
    height: 4rem;
    border-radius: 50%;
    background-color:red;
    display:flex;
    justify-content: center;
    align-items:center;
    color: #f6f6f6;
    font-size:1.4rem;
  }
  
  .music_controls .fa-play:hover {
    background-color:rgb(255, 88, 88);
    color:#fff;
    box-shadow: 0 1rem 2rem 0.2rem rgba(0, 0, 0, 0.4)
  }
  .main-img{
    width:75%;
    height:75%;
    justify-content:center;
    margin-left:3.5rem;
    border-radius:50%;
    box-shadow: 0 1.2rem 3rem 0.5rem rgba(0, 0, 0, 0.4);
  }
  #anime{
    animation: slide 30s  infinite;
    display:flex;
  }
 @keyframes slide{
       0%{
         background-image: url('./assets/Picture/snow.gif');
        ;
       }
        20%{
         background-image: url('./assets/Picture/sun.gif');
        
       }
        40.01%{
         background-image: url('./assets/Picture/chris.gif');
        
       }
       60.01%{
         background-image: url('./assets/Picture/flower.jpg');
         
       }
        80.01%{
         background-image: url('./assets/Picture/madhavan.jpeg');
         
       }
}
  .dropdown{
    text-align:center;
    place-items: bottom;
    display:inline-block;
    margin-top:2rem;
    margin-left:-10rem;
    letter-spacing: 2px;
    padding-left:-5rem;
    word-spacing: 1rem;
    width:400px;
    font-size: 30px;
    font-weight: bold;
    font-style:italic;
    color:rgb(255, 255, 255);
    border: solid 1px rgba(0, 0, 0, 0.2);
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.4);
    background-color:rgba(0, 0, 0, 0.2);
    text-shadow: 1px 1px 2px black, 0 0 25px rgb(255, 17, 0), 0 0 5px rgb(139, 0, 0);
  }  
  .dropdown_content{
    display: none;
    position:absolute;
    background-color: black;
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    padding:12px 16px;
    margin-top:0.5rem;
    margin-left:10rem;
    

  }    
  .dropdown:hover .dropdown_content {
    display: block;
    width:400px;
    margin-left:-2px;
    background-color:black;
  }
  #song-list{
   margin-bottom:-25rem;
    background:black;
    margin-bottom: .8rem;
    margin-left: 8.5rem;
    border: none;
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    font-size:18px;
    text-align: left;
    color: white;
    display: grid;
    font-family:'Philosopher', sans-serif;
  }
  #song-list:hover{
    animation: exam 1s infine;
   box-shadow: 0 4px 8px 0 rgba(245, 232, 232, 0.2), 0 6px 20px 0 rgba(230, 219, 219, 0.19);
  }
  @keyframes exam {
    from { background-color:black;}
    to{ background-color:rgb(124, 121, 121);}
  }   
  .bgimg{
    
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    display:block;
    margin-top: 13.2rem;
    margin-left:-40px;
    place-items: left;
    float:left;

  }
  .omkimg{
    
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    display:block;
    margin-top: -0.1rem;
    margin-left: 70px;
    place-items: left;
    float:left;
  }
  .madimg{
    
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    display:block;
    margin-top: 3.5rem;
    margin-left:-39px;
    place-items: left;
    float:left;
  }
  .myimg{
    
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    display:block;
    margin-top: 6.5rem;
    margin-left:-39px;
    place-items: left;
    float:left;
  }
  .masimg{
    
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    display:block;
    margin-top: 10rem;
    margin-left:-39px;
    place-items: left;
    float:left;
  }
  .artist{
    color:rgba(241, 232, 232, 0.4);
    display: block;
    font-size:14px;
  }
  .pht{
    border-radius:0.3rem;
    height:40px;
    width:40px;
     box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);

  }
  .glow {
  font-size: 80px;
  margin-top:-1rem;
  margin-bottom:2rem;
  color:red;
  text-align: center;
  -webkit-animation: glow 1s ease-in-out infinite alternate;
  -moz-animation: glow 1s ease-in-out infinite alternate;
  animation: glow 1s ease-in-out infinite alternate;
}

@keyframes glow {
  from {
    text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 30px #e60073, 0 0 40px #e60073, 0 0 50px #e60073, 0 0 60px #e60073, 0 0 70px #e60073;
  }
  
  to {
    text-shadow: 0 0 20px #fff, 0 0 30px #ff4da6, 0 0 40px #ff4da6, 0 0 50px #ff4da6, 0 0 60px #ff4da6, 0 0 70px #ff4da6, 0 0 80px #ff4da6;
  }
}
.remoimg{
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    display:block;
    margin-top: 16.5rem;
    margin-left:-39px;
    place-items: left;
    float:left;
}
 .tamimg{
   box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    display:block;
    margin-top: 19rem;
    margin-left:-39px;
    place-items: left;
    float:left;
 }
 .sinimg{
   box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    display:block;
    margin-top: 25rem;
    margin-left:-39px;
    place-items: left;
    float:left;

 }
 .komimg{
   box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    display:block;
    margin-top: 22rem;
    margin-left:-39px;
    place-items: left;
    float:left;
 }
</style>


