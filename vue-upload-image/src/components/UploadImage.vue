<template>
    <div id="upload-image">
        <div v-if="!image">
            <h2>Select an image</h2>
            <input type="file" @change="onFileChange($event)">
        </div>
        <div v-else>
            <img :src="image" />
            <button @click="removeImage(image)">Remove image</button>
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
</style>