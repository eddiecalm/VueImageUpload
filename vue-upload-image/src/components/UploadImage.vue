<template>
    <div id="upload-image">
        <div v-if="!image">
            <h2>Select an image</h2>
            <input type="file" @change="onFileChange($event)" id="upload-image-input-id" hidden>
            <label for="upload-image-input-id"  class="upload-img-btn">Upload</label>
        </div>
        <div v-else>
            <img :src="image" class="img"/>
            <button @click="removeImage(image)" >Remove image</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'upload-image', 
    props: ['image'],
    methods: {
        onFileChange(e) {
            var files = e.target.files || e.dataTransfer.files;
            if (!files.length)
            return;
            this.createImage(files[0]);
        },
        createImage(file) {
            var reader = new FileReader();

            reader.onload = (e) => {
            this.image = e.target.result;
            };
            reader.readAsDataURL(file);
        },
        removeImage: function () {
            this.image = false; 
        }
    } 
}
</script>

<style scoped>
.upload-img-btn {
    background-color: #95C6A4;
    color: #358D4F;
    text-shadow: -1px 0 white, 0 1px white, 1px 0 white, 0 -1px white;
    cursor: pointer;
    width: 150px;
    text-align: center;
    margin: auto;
    border-radius: 5px;
}

.img {
    width: 50%;
}
</style>