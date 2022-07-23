<!-- ---
title: 'Future Development'
subtitle: 'Under Contruction'
date: 2022-02-27 00:00:00
description: This will show software development projects
featured_image: '/images/demo/coding.jpg'
---
![](/images/demo/Under-C.png)
 -->
 
 ---
 title: 'Games'
 date: 2022-07-23 00:00:00
 description: link to games
 ---
 <style>
  fieldset {

    position: absolute;
    border: 10px solid rgb(247, 239, 12);
    width: 1000px;
    height: 600px;
    background-color: white;
    margin: 0 auto;

  }
  legend {
      border: 10px solid rgb(247, 239, 12);
      border: 2px solid black;
      border-radius: 5px;
      width: 150px;
      text-align: center;
      background-color: rgb(247, 239, 12);
      margin: auto;
  }

  p {
      border-left: 6px;
  }

  img {
      position: absolute;
  }

  div {
      position: absolute;
      width: 500px;
      height: 500px;
  }

  #rightSide {
      left: 500px;
      border-left: 1px solid;
  }

  h1 {
      margin-left: 375px;
  }

  body {
      background-image: url(/images/smiley-face-on-black.jpeg);
      background-repeat: no-repeat;
      background-size: cover;
  }
 </style>
 
<body onload="generateFaces()">
  <fieldset>
    <legend>Matching Game</legend>
    <p>Click on the extra smiling face on the left.</p>
    <div id="leftSide"></div>
  <div id="rightSide"></div>
  </fieldset>
  <script>
  let numberOfFaces = 5;
let score = 0;
const theLeftSide = document.getElementById('leftSide');
const theRightSide = document.getElementById('rightSide')

function generateFaces() {
    for (i = 0; i < numberOfFaces; i++) {
        let face = document.createElement('img');
        face.src = 'images/smile.png';

        let randomTop = Math.floor(Math.random() * 400) + 1;
        let randomLeft = Math.floor(Math.random() * 400) + 1;

        face.style.top = randomTop + 'px';
        face.style.left = randomLeft + 'px';
        theLeftSide.appendChild(face);
    }
    const leftSideImages = theLeftSide.cloneNode(true);
    leftSideImages.removeChild(leftSideImages.lastChild);
    theRightSide.appendChild(leftSideImages);
    theLeftSide.lastChild.addEventListener('click', nextLevel);
    document.body.addEventListener('click', gameOver);
}

function nextLevel(event) {
    event.stopPropagation();
    numberOfFaces += 5;
    while (theRightSide.firstChild) {
        theRightSide.removeChild(theRightSide.firstChild);
    }
    while (theLeftSide.firstChild) {
        theLeftSide.removeChild(theLeftSide.firstChild);
    }
    score += 1;
    generateFaces();
}

function gameOver() {
    alert(`Game Over! \n\nYour final score was ${score}`);
    document.body.removeEventListener('click', gameOver);
    theLeftSide.lastChild.removeEventListener('click', nextLevel);
    
    restart = confirm('Click OK to play again')
    if (restart == true){
        document.location.reload()
    } else {
        alert('Goodbye!')
    }  
}
</script>
</body>
  
 
