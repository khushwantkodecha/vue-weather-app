<template>
    <div class="result_container">
        <div class="city_container">
            <h3>
                {{ data.name.toUpperCase() }}
            </h3>
            <h5>
                {{ today.toLocaleDateString("en-US", options) }}
            </h5>
        </div>
        <div class="temp_container">
            <h3>
                {{ data.main.temp }}&#8451;
            </h3>
            <h5>
                {{ data.main.temp_min }} | {{ data.main.temp_max }}
            </h5>
        </div>
    </div>
</template>


<script>
export default {
    name: "ResultView",
    props: {
        data: Object
    },
    data() {
        return {
            today: new Date()
        }
    }
}
</script>


<style>
.result_container {
    height: 40vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
}
</style>
