<script>
  import { page } from "$app/stores";

  export let addressObject;
  import Loading from "$lib/components/common/Loading.svelte";
  import FloatsTable from "$lib/components/common/table/FloatsTable.svelte";
  import Float from "$lib/components/Float.svelte";
  import { getFLOATs } from "$lib/flow/actions.js";
  import { user } from "$lib/flow/stores";

  let floats = async () => {
    const floatsRaw = await getFLOATs(addressObject.address);
    const floatsFormatted = Object.values(floatsRaw || {})?.map((obj) => {
      return {
        totalSupply: obj.totalSupply,
        owner: $page.params.address,
        ...obj.float,
      };
    });
    return floatsFormatted || [];
  };
</script>

<article>
  <header>
    <h3 class="text-center">Claimed FLOATs</h3>
  </header>
  {#await floats()}
    <Loading />
  {:then floats}
    {#if floats.length > 0}
      <FloatsTable {floats} />
    {:else}
      <p class="text-center">This account has not claimed any FLOATs yet.</p>
      {#if $user?.addr == addressObject.address}
        <a href="/create" role="button" class="addnew"
          >Create a new FLOAT Event</a
        >
      {/if}
    {/if}
  {/await}
</article>

<style>
  .addnew {
    font-weight: bold;
    width: 100%;
  }

  @media screen and (max-width: 767px) {
    .addnew {
      margin-top: 20px;
    }
  }
</style>
