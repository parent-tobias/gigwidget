<script>
  export let title;
  export let selected=false;

</script>

<div class="collapse collapse-arrow join-item border border-base-300">
  <input type="radio" name="my-accordion-4" checked={selected} /> 
  <div class="collapse-title text-xl font-medium">{title}</div>
  <div class="collapse-content"> 
    <slot />
  </div>
</div>