<template>
    <div class="grid-container">
        <div v-for="(item, index) in layout" :key="index" class="grid-item">
            <iframe :src="item.url" frameborder="0" width="100%" height="100%"></iframe>
        </div>
    </div>
</template>
  
<script>
import axios from 'axios';

export default {
    data() {
        return {
            layout: [
            ],
        };
    },
    methods: {
        async fetchLayout() {
            try {
                const response = await axios.get('https://mocki.io/v1/3e4532e5-9be2-4923-b43c-bf7182eddc9b');
                this.layout = response.data.websiteData;

                console.log(this.layout); // You can handle the data here or assign it to a variable

            } catch (error) {
                console.error(error);
            }
        },
    },
    mounted() {
        this.fetchLayout();
    },
};
</script>
  
  
<style scoped>
.grid-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(400px, 2fr));
    grid-gap: 10px;
}

.grid-item {
    width: 100%;
    height: 48vh;
}
</style>
  