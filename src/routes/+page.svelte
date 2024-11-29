<script>
     import '../style.css';
     import Todo from './Todo.svelte';
     import Happy from '$lib/images/HomestarHappy.svg';
     import Mad from '$lib/images/HomestarMad.svg';
</script>

<h1>GET TO DOING!</h1>
<h2>With the help of Homestar Runner</h2>
<div class=intro>
     <div>
          <p>Say young man, young man, young man! You look like a fine haver of stuff to do! You wanna get it done? Stop being a total brain-for-brains and get yourself ahead of the game-forest-fire!</p>
          <p>Need a place to write your "To Do" stuff? I got a place to write your "To Do" stuff! Have two places to write your "To Do" stuff! Bwa ha ha! I only got one place to write "To Do" stuff. You get it down and get it done, girl!</p>
     </div>
     <div>
          <img src="{Happy}" alt="Homestar Runner looking happy" height=200px width=200px>
          <div class="thisGuy">
               <p>This Guy</p>
               <p class="arrowd">&#10555</p>
          </div>
     </div>
</div>

<Todo />

<style>
     h1 {
          font-size: 3em;
     }
     h2 {
          font-size: 1.4em;
          margin-top: -1.3em;
     }
     img {
          margin-left: 1em;
     }
     .arrowd {
          font-size: 4em;
          transform:rotate(-60deg);
          display: inline-block;
          margin-top: -0.4em;
          margin-bottom: 0;
     }
     .thisGuy {
          display: flex;
          flex-direction: row;
          font-weight: bold;
          font-family: 'Atma', sans-serif;
          color: #724C00;
          font-size: 1.3em;
          margin-top: -2em;
          margin-left: 3em;
     }
</style>