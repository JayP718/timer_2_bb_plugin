<script>
  import { getContext } from "svelte"
  import Timer from './lib/Timer.svelte';

  const { styleable } = getContext("sdk")
  const component = getContext("component")

  export let endField;
  export let shape;
  export let size;
  export let complete_text;
  export let color;
  export let startField= new Date().getTime(); 
  export let beginField = new Date().getTime();
  export let timeout;
  export let showProgressBar;
</script> 

<div use:styleable={$component.styles}>
  <Timer {endField} {shape} {size} {complete_text} {color} {startField} {beginField} {showProgressBar} on:timeout={timeout}></Timer>
</div>
