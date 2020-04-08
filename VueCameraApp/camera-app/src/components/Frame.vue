<template>
    <div class="picture">
        <canvas></canvas>
    </div>
</template>

<script>
export default {
    name:'frame'
}
</script>

<style lang="scss" scoped>
.picture{
    display: block;
    width:95vw;
    height:95vh;
    padding: 95px;
    box-sizing: border-box;
    canvas {
        display: block;
        width: 100%;
        max-width: 1280px;
        margin: 0 auto;
        box-shadow: 4px 4px 12px 0px transparentize($color: #000000, $amount: 0.5);
    }
}
</style>