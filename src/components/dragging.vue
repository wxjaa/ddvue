<template>
    <div class="wf-dragging-proxy" v-bind:style="cc">
        <div class="proxy-icon">
            <i class="widgeticon" :class="componentName"></i>
        </div>
        <span class="proxy-name">{{componentText}}</span>
    </div>
</template>
<script>
    export default{
        name: 'dragging',
        data: function () {
            return {
                componentName: '',
                componentText: '',
                cc: {},
                isstart: false
            }
        },
        created: function () {
            let self = this
            drag.$on('movestart', function (obj) {
                self.cc = Object.assign({}, self.cc, {
                    display: 'none',
                    top: obj.clientY + 'px',
                    left: obj.clientX + 'px'
                })
                self.componentName = obj.componentName
                self.componentText = obj.componentText
                self.isstart = true
            })
            drag.$on('move', function (obj) {
                if (!self.isstart) {
                    return
                }
                let clientX = obj.clientX
                let clientY = obj.clientY
                let startX = parseInt(self.cc.left);
                let startY = parseInt(self.cc.top);
                let moveX = clientX - startX + 'px'
                let moveY = clientY - startY + 'px'
                self.cc = Object.assign({}, self.cc, {
                    display: 'block',
                    top: startY + 'px',
                    left: startX + 'px',
                    transform: 'translate3d(' + moveX + ',' + moveY + ',0)'
                })
            })
            drag.$on('dragend', function (obj) {
                self.isstart = false
                let startX = self.cc.left;
                let startY = self.cc.top;
                self.cc = Object.assign({}, self.cc, {
                    display: 'none',
                    top: startY + 'px',
                    left: startX + 'px'
                });
                document.querySelector('html').classList.remove('wf-cursor-move');
            })
        }
    }
</script>
