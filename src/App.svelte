<script>
// typewriter efect
 import { onMount } from 'svelte';
 
  function typewriter(node, { speed = 1 }) {
    const valid =
      node.childNodes.length === 1 &&
      node.childNodes[0].nodeType === Node.TEXT_NODE;

    if (!valid) {
      throw new Error(
        `This transition only works on elements with a single text node child`
      );
    }
    const text = node.textContent;
    const duration = text.length / (speed * 0.01);

    return {
      duration,
      tick: (t) => {
        const i = Math.trunc(text.length * t);
        node.textContent = text.slice(0, i);
      },
    };
  }


  // bio 
  let name = "Marcela"; 
  let bio1 = "I am Business Analytics and Economics student in London, interested in leveraging data for social and environmental impact!";
  let showBio = false;

  onMount(() => {
    showBio = true; 
  });

  // hobbies 
  let hobbies = ["Art", "Books", "Studies"]; 
  let selectedCategory = " "; 
  let lists = {
    Art: ["Painting", "Drawing", "Writing"],
    Books: ["TBR:","The perks of being a wallflower - Stephen Chbosky", "A Clergyman’s Daughter - George Owell  ", "Love Letters of Virginia Wolf and Vita Sackville-West - Virginia Wolf & Vita Sackville-West"],
    Studies: ["Data", "French", "Art History "] 
  }

  // fun facts 
  let funfacts = [" 1️⃣ I basically live in two countries during the year (London for uni, Brazil for summer break!)", "2️⃣ I did not know I would be going to study abroad until like 2 months before I had to move!", "3️⃣ The only bone I've ever broken in my body is one of my toes 😅" ];

  // coding journey 
  let codejourney = ["KwK got me started on coding, with the WebDev 2023 Summer Program", "After that, besides going to business school, I decided to take on Business Analytics, to see if I liked it", "Two years later I became obsessed with Data Analytics, Data Science and Storytelling! uniting my love for creativity with a love KwK helped create 💟"];

</script>

<style>
  h1 {
    color: black;
    font-family: Georgia, 'Times New Roman', Times, serif;
    text-align: center;

  }
  h2 {
    color: #2c3e50;
    font-family: Georgia, 'Times New Roman', Times, serif;
  }

  .h-i-header{
    color: darkgreen;
    font-size: 30px;
  }

  .fun-facts-header{
    color: #000052;
    font-size: 30px;
  }

  .bio-container {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    text-align: center;
  }

  .interest {
    background-color: lightgreen;
    border-radius: 10px;
    padding: 10px;
  }

  .hobby-buttons {
    display: flex;
    justify-content: center;
    gap: 15px;
    flex-wrap: wrap;
  }
  .hobby-buttons button {
    background-color: darkgreen;
    color: white;
    padding: 10px 15px;
    border-radius: 10px;
    justify-content: center;
  }


  .hobby-buttons button:hover{
    background-color: white; 
    color: darkgreen;
  }

  .list{
    justify-content: center;
  }


  .fun {
    background-color: lightblue;
    border-radius: 10px;
    padding: 10px;
  }
  .funfacts{
    display: flex;
    align-items: justify;
    justify-content: center;
    gap: 15px;
    flex-wrap: wrap;

  }
  .container{
    display: flex;
    justify-content: space-between;

  }
  .box {
    width: 45%;
    padding: 20px;
    flex: 1;
    margin: 10px;
  }
  .intro{
    font-size: 25px;
    color: black;
  }
  .code{
    background-color: lightyellow;
    border-radius: 10px;
    padding: 10px; 
  }
  .code-header{
    color: darkgoldenrod;
    font-size: 30px;
  }
  .portfolio-link{
    border-style: solid;
    border-color: goldenrod;
		padding: 1rem;             
		border-radius: 8px;        
		display: inline-block;     
		cursor: pointer;           
		transition: background-color 0.3s ease;
  }
  .portfolio-link a{
  color: darkgoldenrod;
  }

  .web-header {
    width: 100%;  
    display: flex;
    justify-content: flex-end;
    gap: 20px; 
    padding: 15px 30px;
    background-color: lightcoral; 
    position: fixed;
    top: 0;
    right: 0;
  }

  .web-header p {
    margin: 0;
  }

  .web-header a {
    text-decoration: none;
    color: darkred;
    font-weight: bold;
  }

  .web-header a:hover {
    color: red; 
  }

  .bio-container {
    text-align: center;
  }

  .image-container {
    position: absolute;
    top: 80px; 
    left: 15px;
}

  .profile-pic {
    width: 200px;     
    height: 200px;
    border-radius: 50%; 
    object-fit: cover;
    flex-shrink: 0; 
}


</style>
<div class="web-header">
  <p class="github web">
    <a href="https://github.com/marcelambicalho" target="_blank">
    github 
  </a>
  </p>
  <p class="linkedin web">
    <a href="https://www.linkedin.com/in/marcela-marques-bicalho/" target="_blank">
    linkedin
  </a>
  </p>
  <p class="email web">
    <a href="mailto:mbicalho821@gmail.com" target="_blank">
    email
  </a>
  </p>
</div>

<div class="image-container">
  <img src="https://i.pinimg.com/736x/a2/6a/27/a26a27a5ff6a2cb80d5b872a73d1413b.jpg" alt="Marcela Marques Bicalho" class="profile-pic" />
</div>

<div class="bio-container">
  <h1>about me</h1>

  {#if showBio}
    <p class="intro" transition:typewriter={{ speed: 1 }}>
      Hi! I'm {name}
    </p>
  {/if}

  <p transition:typewriter={{ speed: 2 }}>{bio1}</p>
</div>



<div class="container"> 
<div class="interest box">
  <h2 class="h-i-header"> hobbies & interests</h2>

  <!-- Buttons for Hobbies Categories -->
  <div class="hobby-buttons">
    {#each hobbies as hobby}
      <button on:click={() => selectedCategory = selectedCategory === hobby ? '' : hobby}>
        {hobby}
      </button>
    {/each}
  </div>
    <!-- Add Functionality -->
    {#if selectedCategory}
      <ul>
        {#each lists[selectedCategory] as list}
        <div class="list">{list}</div>
        {/each}
      </ul>
   {/if}
</div>

<div class="fun box">
  <h2 class="fun-facts-header">fun facts</h2>
  <div class="funfacts">
    {#each funfacts as fact}
      <div class="fact">{fact}</div>
    {/each}
  </div>
</div>
</div>

<div class="code">
  <h2 class="code-header">my coding journey</h2>
  {#each codejourney as journey}
  <div class="journey">{journey}</div>
  {/each} 
  <p class="portfolio-link">
    <a href="https://spice-floor-8a6.notion.site/Marcela-Marques-Bicalho-Data-Strategy-Portfolio-1f1cb013343980498ae5f015e4d339e4?pvs=74" target="_blank">
      <strong>see more here</strong>
    </a>
  </p>
</div>