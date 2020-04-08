<template>
    <div class="camera">
        <video autoplay class="feed"></video>
        <button class="snap" v-on:click="$emit('takePicture')">Capture</button>
    </div>
</template>

<script>
    export default {
        name: "camera",
        methods: {
            init() {
                if ('mediaDevices' in navigator && 'getUserMedia' in navigator.mediaDevices) {
                    let constraints = {
                        video: {
                            width: {
                                min: 640,
                                ideal: 1280,
                                max: 1920
                            },
                            height: {
                                min: 360,
                                ideal: 720,
                                max: 1080
                            }
                        }

                    };
                    navigator.mediaDevices.getUserMedia(constraints).then(stream => {
                        const videoPlayer = document.querySelector("video");
                        videoPlayer.srcObject = stream;
                        videoPlayer.play();
                    });

                } else {
                    alert("Can not Get Media Devices")

                }

            }

        },
        beforeMount() {
            this.init();
        }
    }
</script>


<style lang="scss" scoped>
    .camera {
        width: 95vw;
        height: 95vh;
        padding: 15px;
        box-sizing: border-box;

        .feed {
            display: block;
            width: 100%;
            margin: 0 auto;
            max-width: 1280px;
            background-color: rgb(75, 72, 72);
            box-shadow: 4px 4px 12px 0px rgba($color: #000000, $alpha: 1.0);
        }

        .snap {
            display: block;
            margin: 15px auto;
            width: 75px;
            height: 75px;
            border-radius: 45%;
            background-color: transparentize($color: #f7df09, $amount: 0.1);
            border: 1px solid yellowgreen;
            outline: none;
            cursor: pointer;

            &:hover {
                background-color: lightskyblue;
            }

            &:active {
                background-color: chartreuse;
            }
        }

    }
</style>