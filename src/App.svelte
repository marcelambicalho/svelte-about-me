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
    // Reusable Component //

import ImageCard from "./lib/ImageCard.svelte";
  
  let cardData = [
    {
      image:
        "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBwgHBgkIBwgKCgkLDRYPDQwMDRsUFRAWIB0iIiAdHx8kKDQsJCYxJx8fLT0tMTU3Ojo6Iys/RD84QzQ5OjcBCgoKDQwNGg8PGjclHyU3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3N//AABEIALwAyAMBIgACEQEDEQH/xAAbAAEAAwEBAQEAAAAAAAAAAAAABQYHBAMCAf/EAEAQAAEDAwEEBQcKBAcAAAAAAAEAAgMEBREGEhMhMRRBUWFxByJSgZGhsRYjMjNCU5PB0fA2cnSyFRdVYmOj0v/EABoBAQACAwEAAAAAAAAAAAAAAAACAwEEBQb/xAAuEQACAgIABQMBBwUAAAAAAAAAAQIDBBEFEiExQRNRwRQGFSIjYXGRQkOBkrH/2gAMAwEAAhEDEQA/AKgiIpnlAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAi/V+IAiIg0EREAREQBERAEREAREQBERAfUYDpGg8i4ArUZ9D2RkMjmxzghhI+d7ll8P1rP5h8Vu9Q0vgka36RaQvLfaLKux51enJre/g6vDqoWRlzLZh1toai5VbKWkj25Xnh2AdZPctIg0HaIaVnSzK6RrcvfvNkHt8ApDS2norFSecGvq5B85Jjl2NHcqxrvU5mkktVued2wltRIOBJ9Efmte3PyeJZKpxXyxXd/JZCirGq57Vtlcu0FDPdW0lgp5ZGbWw0l20ZHd3crZZ/J9CGtku8znSHjuonYaPXzKeTK1ximmucjQZC7dRZH0QOZ9/uXbrbVMlpkbRUGz0pzdpz3DIYDy8TzUsvNyrL1g4j6ru/JiqmqNfr2rv4Ol+h7C5mBTSNPaJnZ96qmpNEz2yJ9VQPdUU7RlzSPPYO3vHeuCDWN+il3nTTJk+cyRrSCPZwWl6cvEd8tbKprNl+dmWP0XdioulxPhTVtk+ePnyTgsXK3GK0zIbPTR1V0o6efJjmmYx4BwcEgFaV8hLGDxjm8N8VWLjbI7Vr2jjhbswzVEcrGjkMu4j2grQL9US0tkrZ4HlssULnMdzwQFPi+fdZOl482lNEcOiEVP1FvRCv0FZCMBtQ3vEigL3oGanidNapjUADO5eMPPh1FRMWsr8x7T0/bxzDo2kH3LQtKX8X6he9zBHURO2ZWg8D2EdxUb/vbhqV0580fJKv6TJfIo6ZkUMYdUxxPB4vDXDrHFaj8g7H93N+Mq3rq3MotR01TC0BlUQ5wHpA8fiFpM+86PJufrNk7Pis8Y4lbOumymTjzGMTGgpTjNb0Vv5B2P7uf8Up8g7H93P8AilQGde/8/sjXnPU63p4JZp3zsjjaXPdsx8AFXCjNbWsqP+xlzoX9p/wU1wAcQO0r5Qkk5KL28exxGERFkBERAEREAREQH3D9az+YfFb3nBwsEh+tZ/MPit3qHFlNIW8CGEj2Lx32qXNKpfv8HZ4W9KbPGnuFLUVk9JDO100GDIwfZz+/gqB5RLEaaf8AxWlZ81KdmcD7LvS8D8VWrNdp7XdIq+NznuB+cyfptPMFbCOi3q1Z4S0tTH7v1/MLVnRZwTJhbF7g+/yWxsjm1uL7ohfJ1K2TTcbGkZjmeHeOc/mqj5RaaSLUb5X53c8bXRk8uAwR7l1Wask0bf57fXZNJKfrMdXHD/19fYr3X2+3XujaypYyeF3Frmu5d4IUpX/d/EHla3XPz+jMKHr4/pdpRMSxlvZ4rTfJnTSRWeeZ4wyaXLP9wAxn99i9qfQNmin3julSj0JJBj3AFTFzudDYqDeTFrGMbsxxNHF3cArOK8Xhn1rHxottsji4kqJOyx9irarmY/XFmjYQXRui2u7L+Xu96s+p/wCHbj/Tv+CzKhrpblq+jrajAkkq4zsjkBtAALWq2ljrqSWlmJEcrCx2z3rU4nV9HLGjP+ldf5LcWXrKxryYRz5rQvJbA8RXCctIieWMaepxGc/FScWgbI0hxFS8ei6TgfZgqbkkoLJb8kx01LGOAxj2dpW5xTjdeZR9PRFtspxcKdM/Um+iKl5SZGdNs0Q4vD3E9wJbhXl72xRue4+a0ZJ9Sx683d97v7Ktw2Yg9rYm9jQeHrJWwzRiaN0T+DXDB8FocVxnjY+PXZ7PZsYtnqWWSiVz5c2H7+X8IrivOsLPWWetpoZpDLJC9jQYiMkhe3+X9m9Oq/FH6I7yf2UjBdV/iD9FKp8HhJSTltEZrMaa6aMtRe1XE2GqmjYctY9zQfAleK9/BqUU0efa0wiIpAIiIAiIgCIiA+m52wWcSDkYVouF+1ZRwA18+6bJ5oa+KMOPDsxkKrx8HjPLKtesarpNBTjYEYa/kZ45XHgfth7nH1geK5uaoytrjKCffv8ABs07UJNNoh6zT9zoqDptVTbumIGH7xp58uAKk9My6qdROjsm0aVjyTkMwD2Au/JXmutRu+naSi2920tiL3deBjl3qN1bdG6atMFvtcW6fI3ZY8DgwDme8rhri8stLH5FKbb6PskvJvfSKr8zmajoq1ZS6l1BUyQTsZUzUWGvDXRDY2uokc+Sjqa53axTyU9PUyU74nFj48hzWkdWDwVq8lZJkuhcck7oknr+mqjqL+ILl/VSf3FdLGsVmTZhzguWKXj3Naxctcbot7ZJy63vsjA0VETXcPObEM+8LzbYtRX09Llgml2hwfUPDfYCeC6NAWuG43h0lU1r4aZm3sEcC48B+ZUzqjWlXRXOShtkcTWwHZc97cknsCots9LJ+nwao82tt+xZCPPX6l8noqNXb7pYKuGaop3wSMeHRyYDm5Bzz5KTpdU6nq5xBTVDpZXcmMgjJ/t5K3aau8eqrbVUtygj22AB7WjDXNPWOxR/k/ghoLxd6KRwNTE8NY483MBcCR7lTbnqVdiyaU7If57+ScaNSj6c2oyPGc69ZAXucS3rDBCXBUuuq62snPTpZ5ZWuxiUklp8O1adLPqaju75ZIWVdtLjhkAbtMZ1YzgkqqRXGCu15TVVXRikbvNl0b+e1g7Jd68LHDsnXNP04dFvcf8AgyK+y5n311OGk0lfpmRzxUbmAecN49rTnwKkm3fWRuHQDK5tUQXCN0cTcgc8EgZVu1GNRNkhlsL4TG0fORPDQ5xz2nqVX1jfqkTUQdbZKSpp3NlE0nPaxxa3uVdOZdnyXPCEt717r99kp0QoXSTXyc1zv2rrTJHFcKgwveMtzHE7PVzA/fBe9vuetrlS9KpJTJBkjbLYWjhzxkD95VhraWn1lp+nljeI5NoEHnsHk9p/fYuPW1xis1lhs1vIa+RmyQ08WRjmfX+qrqyK7XGmNEfV3p9Oi15JSrlBObm+XXTqZxK90kj5HnLnuLnHtJ5r4RF7FLS0cZhERZAREQBERAEREB9N4uaOHPrU/fB0e0QxGnoYjJMJWikm2w5uDx4uKrwODldtfdau4RsZVOjc1gw3ZhYwgdmWgcO5at9M7Jxa7IuhNKLTNRu10ks+lIquFodI2KNrc8gSBxXKw0+s9MYOy2qZw74pR+R+B7ln9ZqC6VtCKGpqtumaGgM3bBy5cQMrxtl3r7S+R9vqDEZBh3mtcD6iCuBDgNkK+aLSsUtp/p7G88+Mpaa/DrRdPJlDJTVN3gmYWSxmNr2nqPnLiu2ibvV3WrqYujbuaZ725kOcE57FBQ6nvENVPUxVYbNOGiVwhZ52znHV3le/yzv/APqH/TH/AOVdLB4hHKlkVOO5Jb7kFfjutVzT6E7pumn0neo4bs6JsVdGWMcx2Q1zSOftXrqjRdZW3OWvtzoXCY7T2SOxg9ZB61TbpebhdzF/iFRvd1nY8xrcZx2AdgXXQ6pvNDCIoK0mMcmSNDsesjKlLAzlYsmE16jWn7Mwsijldck+Xx7l601Z2aUt1TWXGoZtvAMhaeDQOQHaeKi9L0NBfpbhcnTysuEkry0B2yYc8iMc/XwVPud5uN0I6fVySgcm8A32DguakrKiinE1JM+GQfaYcLC4RkShZOdn5svbt08GXl1qUVGP4UaZaYtXwXJkVfLBUUYd50jiMkd2BnPivPUNBablquhp66TEpgJLW4G8ORsgnq61UHa1v5jLTWDiMbQiZn4KDlqJppnTSyvfK520Xl3HPiqaODZLtdkmovWvw/JOeZWoqKTfXyaXWW/VFBWuFkqRNROdlsUhad2Owl3H2L110WnSeK7dipzHshvLeZG1s93NUmn1hfYI2sFeXhvLeMa4+0jKjbjda65yCSvqXzEcgcADwA4JTwbJ9eE7XFKL7ru/3E8yrkko76+/ZFx8lsr95Xw7R3YDH7PVniMqs6tkfNqO4b1xdsyljc9QHILmtV3r7Q+R9vn3TpAA87DXZx4grmqqiWrqZKioftyyuLnuwBknwXTpwJQz55L1po1p3qVEa/KPJERdU1AiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIBkoiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiAIiIAiIgCIiA//2Q==",
      title: "2023",
      description:
        "KwK got me started on coding, with the WebDev 2023 Summer Program",
    },
    {
      image: 
      "https://static1.squarespace.com/static/623126b50d2dfb281caaafd3/6255f88148b14a5350d7c886/62d19f561a31d8261ecb4b50/1731347881085/Hult-International-Business-School-logo.jpg?format=1500w",
      title: "2024",
      description: "After that, besides going to business school, I decided to take on Business Analytics, to see if I liked it",
    },
    {
      image: 
      "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQrWez0BExIGF0Ct2CM5qwh6JF6LAoIeSPZ3A&s",
      title: "2025",
      description:
        "Two years later I became obsessed with Data Analytics, Data Science and Storytelling! Combining my love for creativity with a love KwK helped create 💟.",
    },
  ];

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
    border-color: darkgreen;
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

  .card-container{
    display: flex; 
    justify-content: center;
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
  <div class="card-container">
  {#each cardData as { image, title, description }}
    <ImageCard {image} {title} {description} />
  {/each}
  </div>  
  <p class="portfolio-link">
    <a href="https://spice-floor-8a6.notion.site/Marcela-Marques-Bicalho-Data-Strategy-Portfolio-1f1cb013343980498ae5f015e4d339e4?pvs=74" target="_blank">
      <strong>see more here</strong>
    </a>
  </p>
</div>