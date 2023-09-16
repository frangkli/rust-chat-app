<script lang="ts">
  let users = new Map<string, { online: boolean; selected: boolean }>([
    [
      "User 1",
      {
        online: true,
        selected: false,
      },
    ],
    [
      "User 2",
      {
        online: false,
        selected: false,
      },
    ],
    [
      "User 3",
      {
        online: true,
        selected: false,
      },
    ],
    [
      "User 4",
      {
        online: true,
        selected: false,
      },
    ],
    [
      "User 5",
      {
        online: false,
        selected: false,
      },
    ],
  ]);

  function addToGroup(event: Event) {
    const button = event.target as HTMLButtonElement;
    const username = button.innerText;
    users.get(username).selected = !users.get(username).selected;
    users = users;
  }

  $: selected = Array.from(users.keys())
    .filter((user) => users.get(user).selected)
    .join(", ");
</script>

<div>
  <div class="users">
    {#each users.keys() as user}
      {#if users.get(user).online}
        <button
          on:click={addToGroup}
          class={users.get(user).selected ? "selected-button" : ""}
          >{user}</button
        >
      {/if}
    {/each}
  </div>
  Select users to make a group chat.
  <p class="selected-list">
    {selected && ` Selected: ${selected}`}
  </p>
</div>

<style>
  .users {
    margin: 1em 2em 1em 2em;
    line-height: normal;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(2, 1fr);
    gap: 1em;
    justify-content: center;
    text-align: center;
  }
  .selected-button {
    background-color: #4caf50;
    color: white;
  }
  .selected-list {
    font-style: italic;
  }
</style>
