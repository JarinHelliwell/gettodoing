<script>
     import '../style.css';
     import Todo from './Todo.svelte';
     import Happy from '$lib/images/HomestarHappy.svg';
     import Mad from '$lib/images/HomestarMad.svg';
</script>

<h1>Get to Doing!</h1>
<div class=intro>
     <div>
          <p>Say young man, young man, young man! You look like a fine haver of stuff to do! You wanna get it done? Stop being a total brain-for-brains and get yourself ahead of the game-forest-fire? </p>
          <p>Need a place to write your to do stuff? I got a place to write your to do stuff! Have two places to write your to do stuff! Bwa ha ha! I only got one place to write to do stuff. You get it done, girl!</p>
     </div>
     <div>
          <img src="{Happy}" alt="Homestar Runner looking happy" height=200px width=200px>
     </div>
</div>

<Todo />

<style>
     .intro {
          display: flex;
          align-items: center;
          margin: 0em 4em 2em 4em;
     }
     .intro img {
          padding: 2em;
     }
</style>