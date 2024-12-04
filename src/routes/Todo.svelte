<!-- Component -->
<script>
     import {onMount} from 'svelte';
     let todoItem = $state('');
     let todoList = $state([]);
     let storedList;

     onMount(() => {
          storedList = localStorage.getItem('storedList');
          if (storedList) {
               todoList = (JSON.parse(storedList));
          }
     })

     function updateList() {
          return storedList = localStorage.setItem('storedList', JSON.stringify(todoList));
     }

     function cap(w) {
          return w.charAt(0).toUpperCase() + w.slice(1);
     }

     function addItem(event) {
          event.preventDefault();
          if (todoItem == '') {
               return;
          }
          todoList = [...todoList, {
               text: cap(todoItem),
               done: false,
          }];
          updateList();
          todoItem = '';
     }

     function removeItem(index) {
          todoList = todoList.toSpliced(index, 1);
          updateList();
     }

     function nuke(){
          todoList = [];
          localStorage.clear();
     }

     function wrongWord(){
          const text = document.getElementById("baleeted");
          text.style.display = "block";
     }

     $inspect(todoList);

     import Yay from '$lib/images/HomestarHappy2.svg';
     import Mad from '$lib/images/HomestarMad.svg';

</script>

     <div class=adder>
          <h2>What Is It? What Is It? What Is It?</h2>
          <form onsubmit={addItem}>
               <input id="addToDoItem" type="text" bind:value={todoItem}>
               <button type="submit">Add</button>
          </form>
     </div>

     <ul>
          {#each todoList as item, index}
               <li>
                    <div class="motivate">
                    {#if (item.done)}
                         <img src="{Yay}" alt="Homestar Runner looking happy" height=135px width=135px>
                         <p>Hurray! All done!</p>
                    {:else}
                         <img src="{Mad}" alt="Homestar Runner looking mad" height=135px width=135px>
                         <p>Still gotta do!</p>
                    {/if}
                    </div>
                    <input class="checkplease" type="checkbox" bind:checked={item.done} onchange={updateList}>
                    <span class:done={item.done}>{item.text}</span>
                    <button class="removeX" type="button" onclick={() => removeItem(index)}>X</button>
               </li>
          {/each}
     </ul>

     {#if (todoList.length == 0)}
          <button type="button" class="clear" onclick={wrongWord}>BALEETED!</button>
          <p id="baleeted" class="baleeted">Oh, um... That's the wrong word.</p>
     {:else}
          <button type="button" class="clear" onclick={nuke}>DELETED!</button>
     {/if}

<!-- Styles in here will only apply to this one component, not the entire app -->
<style>

</style>