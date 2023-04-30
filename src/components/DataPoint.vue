<template>
    <div>
        <span>🌡️ {{ Math.round(temperature*100)/100 }}</span>
        <span>🇺🇸 {{  zip_code }}</span>
        <span>🌐 {{ lat }}, {{ long }}</span>
        <span>💧 {{  humidity }}</span>
        <span>🤖 {{ sensor_id }}</span>
    </div>
</template>

<style scoped>
div > span {
    display:inline-flex;
    margin: 5px;
    padding: 5px;
    border-radius: 4px;
    border: 1px solid #9f9f9f;
    font-size: large;
}
div {
    /* display: table-row; */
    /* display: flex; */
    padding: 3px;
    margin-top: 5px;
    margin-bottom: 5px;
    justify-content: space-between;
}

div:hover {
    background-color: #f5f5f5;
}
</style>
<script>
export default {
  name: 'DataPoint',
  props: {
        temperature: Number,
        zip_code: String,
        lat: Number,
        long: Number,
        humidity: Number,
        sensor_id: Number,
  }
}</script>