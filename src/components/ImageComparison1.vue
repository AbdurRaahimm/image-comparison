<script setup>
const sliderChange = (e) => {
    const slider = e.target;
    const afterImage = document.querySelector('#image2');
    afterImage.style.clipPath = `polygon(0 0, ${slider.value}% 0, ${slider.value}% 100%, 0 100%)`;
};

const image2Preview = (e) => {
    const file = e.target.files[0];
    const reader = new FileReader();
    reader.onload = (e) => {
        const afterImage = document.querySelector('#image2');
        afterImage.src = e.target.result;
    };
    reader.readAsDataURL(file);
};

const image1Preview = (e) => {
    const file = e.target.files[0];
    const reader = new FileReader();
    reader.onload = (e) => {
        const beforeImage = document.querySelector('#image1');
        beforeImage.src = e.target.result;
    };
    reader.readAsDataURL(file);
};


</script>

<template>
    <div class="mb-3">
        <h1 class="text-3xl font-bold text-center capitalize">online image comparision</h1>
        <p class="text-sm text-center text-gray-500">Drag the slider to compare the images</p>
    </div>
    <div class="flex flex-col space-y-3 sm:space-y-0 sm:flex-row justify-center items-center ">
        <!-- image upload -->
        <div class="">
            <label for="img1" class="custom-file-upload">
                <i class="fa fa-cloud-upload"></i> Image 1
            </label>
            <input @change="image1Preview" name="img1" type="file" />
        </div>

        <div class="">
            <label for="img2" class="custom-file-upload">
                <i class="fa fa-cloud-upload"></i> Image 2
            </label>
            <input @change="image2Preview" name="img2" type="file" />
        </div>

    </div>
    <div class="relative w-full h-full sm:w-6/12 mx-auto mt-6">
        <figure class="relative">
            <img id="image1" src="https://plus.unsplash.com/premium_photo-1669863284071-06345764d4c2?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                alt="image1" class=" h-auto " />
            <!-- <figcaption class="absolute top-0 left-3 text-white text-xl font-bold">Image 1</figcaption> -->
        </figure>
        <figure class="absolute top-0">
            <img id="image2" style="clip-path: polygon(0 0, 50% 0, 50% 100%, 0 100%);"
                src="https://plus.unsplash.com/premium_photo-1669863280125-7789ef60adc0?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="image2" class="h-auto " />
            <!-- <figcaption class="absolute bottom-0 left-3 text-white text-xl font-bold">Image 2</figcaption> -->
        </figure>
        <input @input="sliderChange" type="range" min="0" max="100" value="50"
            class="absolute top-0  outline-none slides" />
    </div>

</template>