<!-- Component -->
<script>
     let todoItem = $state('');
     let todoList = $state([]);

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
          todoItem = '';
     }

     function removeItem(index) {
          todoList = todoList.toSpliced(index, 1);
     }

     function nuke(){
          todoList = [];
     }

     $inspect(todoList);

     import Yay from '$lib/images/HomestarHappy2.svg';
     import Mad from '$lib/images/HomestarMad.svg';

</script>

     <div class=adder>
          <h2>What Is It? What Is It? What Is It?</h2>
          <form onsubmit={addItem}>
               <input type="text" bind:value={todoItem}>
               <button type="submit">Add</button>
          </form>
     </div>

     <ul>
          {#each todoList as item, index}
               <li>
                    <div class="motivate">
                    {#if (item.done)}
                         <img src="{Yay}" alt="Homestar Runner looking happy" height=150px width=150px>
                         <p>"You about to win!"</p>
                    {:else}
                         <img src="{Mad}" alt="Homestar Runner looking mad" height=150px width=150px>
                         <p>"Keep on doing it!"</p>
                    {/if}
                    </div>
                    <input type="checkbox" bind:checked={item.done}>
                    <span class:done={item.done}>{item.text}</span>
                    <button type="button" onclick={() => removeItem(index)}>X</button>
               </li>
          {/each}
     </ul>

     {#if (todoList.length == 0)}
          <button disabled type="button" class="clear">BALEETED!</button>
     {:else}
          <button type="button" class="clear" onclick={nuke}>DELETED!</button>
     {/if}

<!-- Styles in here will only apply to this one component, not the entire app -->
<style>
     .adder input {
          height: 1.4em;
          font-size: 1.4em;
          margin-left: 2em;
     }
     ul {
          list-style: none;
          align-self: flex-start;
          margin-left: 4vw;
     }
     li {
          display: flex;
          align-items: center;
          font-family:Arial, Helvetica, sans-serif;
          margin: 2vw 10vw 2vw 15vw;
     }
     .motivate {
          margin-right: 2vw;
     }
     .motivate p {
          font-size: 0.8em;
          margin-top: -0.3vw;
     }
     span {
          margin: 2vw 6vw 2vw 2vw;
          font-size: 1.4em;
     }
     span.done {
          color: grey;
          text-decoration: line-through;
     }
     .clear {
          margin: 10vw 15vw;
     }
</style>