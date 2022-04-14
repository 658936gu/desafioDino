# desafioDino
const dino = document.quarySelector('.dino');
const background = document.querySelector('background');
let isjumping = false;
let position = 0;

function handlekeyUp(Event) {
  if (Event.keyCode === 32) {
    if(!isjumping) { 
    jump();
    }
  }            
} 

function jump(){
   isjumping = true;
   let position = 0;
    
   let upInterval = setInterval(() => {
     if (position >= 150){
        clearInterval(upInterval);
          
        let dowInterval = setInterval(() => {
          if (position <= 0) {
            clearInterval(dowInterval);
            isjumping = false;
            } else {
              position -= 20;
              dino.style.botton = position + 'px';
            }
           }, 20);
        } else { 

         position += 20; 
         dino.style.botton = position + 'px';
    }
  }, 20);
}

function creatcactus(){
  const cactus = document.creatElement('div'); 
  let cactusPositin = 1000;
  let randomtime = Math.random() + 6000;

  cactus.classList.add(cactus);
  cactus.style.left = 1000 + 'px';
  background.appendChild(cactus);

  let leftInterval = setInterval(() => {
        if (cactusPositin < -60){
      clearInterval(leftInterval);
      background.removeChild(cactus);
    } else if (cactusPositin > 0 && cactusPositin < 60 && position < 60) {

      clearInterval(leftInterval);
      document.body.innerHTML = <h1 class ='game-over'></h1>;
    } else {
     cactusPositin -= 10;
     cactus.style.left = cactusPositin + 'px'; 
    }
  }, .20);
}
setTimeout(() => {
  
}, timeout(creatcactus, randomTime));
creatcactus();
document.addEventListener('keyup', handlekeyUp); 
