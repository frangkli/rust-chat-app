<script lang="ts">
  import Join from "./lib/Join.svelte";
  import Users from "./lib/Users.svelte";
</script>

<main class="container">
  <h1>Welcome to the useless chat app!</h1>

  <h2>Online Users</h2>

  <Users />

  <div class="row">
    <Join />
  </div>
</main>
