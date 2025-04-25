<script lang="ts">
  import { filter_params, time_filter } from "../stores/filters";

  export let value: string;
  export let label: string;

  // Track if the time filter is active
  let isActive = false;

  // Update isActive whenever filter_params changes
  $: {
    isActive = $filter_params.time === value;
  }

  function setTimeFilter() {
    if (isActive) {
      time_filter.set("");
    } else {
      time_filter.set(value);
    }
  }
</script>

<a href={"#"} on:click|preventDefault={setTimeFilter} class:active={isActive}
  >{label}</a
>

<style>
  a:link {
    color: #66c4ff;
  }

  a:link:hover {
    color: #737373;
  }

  a.active {
    font-weight: bold;
    text-decoration: underline;
  }
</style>
