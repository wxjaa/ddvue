<template>
    <div id="app" class="wf-wrapper" v-on:mouseup="moveend" v-on:mousemove="move">
        <Header></Header>
        <div class="wf-main">
            <mainleft></mainleft>
            <formcanvas></formcanvas>
            <setting></setting>
        </div>
        <dragging></dragging>
    </div>
</template>

<script type="text/ecmascript-6">
    import Header from './components/header'
    import mainleft from './components/mainLeft'
    import formcanvas from './components/formcanvas'
    import setting from './components/setting'
    import dragging from './components/dragging'

    export default {
        name: 'app',
        components: {
            Header,
            mainleft,
            formcanvas,
            setting,
            dragging
        },
        data: function () {
            return {
                isstart: false,
                componentView: {}
            }
        },
        methods: {
            move: function (e) {
                if (this.isstart) {
                    document.querySelector('html').classList.add('wf-cursor-move')
                    drag.$emit("moveInCanvas", e)
                    drag.$emit('move', e)
                }
            },
            moveend: function (e) {
                if (this.isstart) {
                    let obj = {
                        componentView: this.componentView
                    }
                    drag.$emit("moveend", obj)
                    this.isstart = false
                }
            }
        },
        created: function () {
            let self = this
            drag.$on('movestart', function (obj) {
                self.isstart = true
                self.componentView = obj.componentView
            })
        },
        mounted: function () {

        }
    }
</script>
<style>
    @import "style/design.css";
</style>
<style>
    #app {
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
    }
</style>
