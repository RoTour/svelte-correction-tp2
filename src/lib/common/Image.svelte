<script lang="ts">
  import { createEventDispatcher } from "svelte";

  export let src = "";
  export let alt = "";
  let element: HTMLImageElement;
  let dispatch = createEventDispatcher();

  const notifyLoaded = () => {
    element.removeEventListener("load", onload.bind(null, element));
    dispatch("loading", false);
  };

  const onload = (el: HTMLImageElement) => {
    element = el;
    dispatch("loading", true);
    el.addEventListener("load", () => {
      notifyLoaded();
    });
  };

  $: if (src && element) {
    onload(element);
  }
</script>

<img use:onload {src} {alt} />
