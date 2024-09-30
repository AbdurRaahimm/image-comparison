<script setup>

const sliderChange = (e) => {
  const slider = e.target;
  const afterImage = document.querySelector('img[alt="After"]');
  afterImage.style.clipPath = `polygon(0 0, ${slider.value}% 0, ${slider.value}% 100%, 0 100%)`;
};



</script>

<template>

<div class="grid place-items-center overflow-hidden">
  <div class="relative h-[30rem] w-[44rem] ">
    <img
      src="https://i.pinimg.com/originals/e8/29/6d/e8296d02a448463f95b14ec93aa0f16c.jpg"
      alt="Before"
      class="w-full h-auto absolute "
    />
    <img
      src="https://my.alfred.edu/zoom/_images/foster-lake.jpg"
      alt="After"
      class="w-full h-auto absolute "
      style="clip-path: polygon(0 0, 50% 0, 50% 100%, 0 100%);"
    />

    <input
    @input="sliderChange"
      type="range"
      min="0"
      max="100"
      value="50"
      class="slider" 
  </div>
</div>

</template>

<!-- https://i.pinimg.com/originals/e8/29/6d/e8296d02a448463f95b14ec93aa0f16c.jpg
https://my.alfred.edu/zoom/_images/foster-lake.jpg -->