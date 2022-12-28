<script>
    import { getContext,createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    export let endField;
    export let shape;
    export let size;
    export let complete_text;
    export let color;
    export let startField;
    export let beginField;
    export let showProgressBar;
  
    const component = getContext("component");
    const { styleable } = getContext("sdk");
  
  
    let reduceDistance = setInterval(
      () =>
        distance <= 0
          ? (dispatch('timeout'),
            clearInterval(reduceDistance))
          : (distance = distance - 1000),
      1000
    );
    $: totalDistance =  Math.round((endField-beginField)/1000)*1000;
    $: distance =  Math.round((endField-startField)/1000)*1000;

    
    $: days = Math.floor(distance / 86400000);
    $: hours = Math.floor(((distance) % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    $: minutes = Math.floor(((distance) % (1000 * 60 * 60)) / (1000 * 60));
    $: seconds = Math.floor(((distance) % (1000 * 60)) / 1000);
  </script>
  
  <div use:styleable={$component.styles}>
    <div class="progress-btn" data-progress-style="fill-back" style="border-radius: {shape};  font-size: {size};  background-color: {color};">
      <div class="btn">
        {#if ((totalDistance-distance)/totalDistance)  >= 1} {complete_text} {/if}
        {#if days > 0} {days} days {/if}
        {#if hours > 0} {hours} hrs {/if}
        {#if minutes > 0} {minutes} mins {/if}
        {#if seconds > 0} {seconds} secs {/if}
      </div>
      
  
      {#if showProgressBar && (((totalDistance-distance)/totalDistance) * 100 <= 100)}
      <div
      class="progress"
      style="width: {((totalDistance-distance)/totalDistance)*100}%"
    />
      {:else}
    <div></div>
      {/if}
  
     
    </div>
  </div>
  
  <style>
   
  
    .progress-btn {
      position: relative;
      width: 100%;
      height: 50px;
      display: inline-block;
      background: #f44336;
      font-family: "RobotoDraft", "Roboto", sans-serif;
      color: #fff;
      font-weight: normal;
      font-size: 20px;
      transition: all 0.4s ease;
    }
  
    .progress-btn .btn {
      position: absolute;
      left: 0;
      top: 0;
      right: 0;
      bottom: 0;
      line-height: 50px;
      text-align: center;
      z-index: 10;
      opacity: 1;
    }
  
    .progress-btn .progress {
      z-index: 5;
      background: black;
      opacity: 70;
      transition: all 0.3s ease;
    }
  
    .progress-btn[data-progress-style="fill-back"] .progress {
      position: absolute;
      left: 0;
      top: 0;
      right: 0;
      bottom: 0;
    }
  </style>
  