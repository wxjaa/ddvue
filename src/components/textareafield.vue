<template>
    <div class="wf-widgetsitem" data-type="textfield" v-on:mousedown="start">
        <label>
            多行输入框
        </label>
        <i class="widgeticon textareafield"></i>
    </div>
</template>
<script>
    export default{
        name: 'textareafield',
        data: function () {
            return {
                offsetTop: 0,
                offsetLeft: 0,
                componentView: {
                    name: '多行输入框',
                    defaultLable: '多行输入框',
                    defaultProps: '请输入',
                    defaultImportant: false,
                    componentName: 'textareafield',
                    supportSetting: ['label', 'placeholder', 'required', 'important', 'print']
                }
            }
        },
        methods: {
            start: function (e) {
                let obj = {}
                let dom = e.currentTarget
                var actualLeft = dom.offsetLeft;
                var current = dom.offsetParent;
                while (current !== null) {
                    actualLeft += current.offsetLeft;
                    current = current.offsetParent;
                }
                var actualTop = dom.offsetTop;
                var current = dom.offsetParent;
                while (current !== null) {
                    actualTop += current.offsetTop;
                    current = current.offsetParent;
                }
                obj.componentName = dom.getAttribute("data-type")
                obj.componentText = dom.querySelector('label').innerText
                obj.clientX = e.clientX
                obj.clientY = e.clientY
                obj.isstart = true
                obj.componentView = this.componentView
                drag.$emit("movestart", obj)
            }
        }
    }
</script>
