<template>
    <div class="wf-widgetsitem" data-type="numberfield" v-on:mousedown="start">
        <label>
            数字输入框
        </label>
        <i class="widgeticon numberfield"></i>
    </div>
</template>
<script>
    export default{
        name: 'numberfield',
        data: function () {
            return {
                offsetTop: 0,
                offsetLeft: 0,
                componentView: {
                    name: '数字输入框',
                    defaultLable: '数字输入框',
                    defaultProps: '请输入',
                    defaultImportant: false,
                    componentName: 'numberfield',
                    supportSetting: ['label', 'placeholder', 'required', 'important', 'print','uint']
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
