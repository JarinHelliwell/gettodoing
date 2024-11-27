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

</script>

     <div class=adder>
          <h2>Whatcha Got?</h2>
          <form onsubmit={addItem}>
               <input type="text" bind:value={todoItem}>
               <button type="submit">Add</button>
          </form>
     </div>

     <ul>
          {#each todoList as item, index}
               <li>
                    <input type="checkbox" bind:checked={item.done}>
                    <span class:done={item.done}>{item.text}</span>
                    <button type="button" onclick={() => removeItem(index)}>X</button>
               </li>
          {/each}
     </ul>

     {#if (todoList.length == 0)}
          <button disabled type="button" class="clear">Burninate!</button>
     {:else}
          <button type="button" class="clear" onclick={nuke}>Burninate!</button>
     {/if}

<!-- Styles in here will only apply to this one component, not the entire app -->
<style>
     .adder {
          display: flex;
          align-items: center;
          flex-direction: column;
     }
     ul {
          list-style: none;
     }
     span.done {
          color: grey;
          text-decoration: line-through;
     }
     .clear {
          margin: 0em 44vw;
     }
</style>