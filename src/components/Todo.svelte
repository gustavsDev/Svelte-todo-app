<script>
 let list = [];
 let value = "";

 function addTODO() {
   if(value == "") return;
   list = [...list, value];
   value = "";
 }

 function deleteTODO(i) {
   list = list.splice(i, 1);
 }
</script>

<ul>
  {#each list as item, i}
  <li><img width="20" height="20" src="https://img.icons8.com/ios-filled/50/circled-x.png" alt="circled-x" class="red img_button" style="margin-right: 1rem;" on:click={() => { deleteTODO(i); }} /> {item}</li>
  {/each}
</ul>

<div>
  <input type="text" name="value" bind:value={value}>
  <button on:click={addTODO}>Add</button>
</div>

<style>
  ul {
    text-decoration: none;
  }  

  li {
    display: flex;
    flex-direction: row;
    align-items: center;
  }

  li:before {
    content: "";
    width: 2px;
    height: 1rem;
    position: relative;
    left: calc(20px + 0.5rem);
    background-color: black;
  }

  .red {
    filter: invert(62%) sepia(66%) saturate(3087%) hue-rotate(318deg) brightness(97%) contrast(112%);
  }

  .img_button {
    cursor: pointer;
  }
</style>
