<script>
 let list = [];
 let value = "";

 function addTODO() {
   if(value == "") return;
   list = [...list, value];
   value = "";
 }

 function deleteTODO(i) {
   list = list.filter((item, index, arr) => {
     return i != index;
   });
 }
</script>

<div>
  <input type="text" name="value" bind:value={value}>
  <button on:click={addTODO}>Add</button>
</div>

<ul>
  {#each list as item, i}
    <li>
      <button type="button" style="margin-right: 1rem;" on:click={() => { deleteTODO(i); }}>
        <img width="20" height="20" src="https://img.icons8.com/ios-filled/50/circled-x.png" alt="circled-x" class="red img_button">
      </button>

      {item}
    </li>
  {/each}
</ul>

<style>
  ul {
    text-decoration: none;
  }  

  li {
    display: flex;
    flex-direction: row;
    align-items: center;
  }

  li button {
    background: none;
    border: none;
  }

  li:before {
    content: "";
    width: 2px;
    height: 20px;
    position: relative;
    left: 2rem;
    background-color: #AAA;
  }

  .red {
    filter: invert(62%) sepia(66%) saturate(3087%) hue-rotate(318deg) brightness(97%) contrast(112%);
  }

  .img_button {
    cursor: pointer;
  }
</style>
