<template>
    <div class="wf-widgetsitem" data-type="dddatefield" v-on:mousedown="start">
        <label>
            日期
        </label>
        <i class="widgeticon dddatefield"></i>
    </div>
</template>
<script>
    export default{
        name: 'dddatefield',
        data: function () {
            return {
                offsetTop: 0,
                offsetLeft: 0,
                componentView: {
                    name: '日期',
                    defaultLable: '日期',
                    defaultProps: '请选择',
                    defaultImportant: false,
                    defaultFormat: 'yyyy-MM-dd',
                    componentName: 'dddatefield',
                    supportSetting: ['label', 'placeholder', 'dateformat','required', 'important', 'print']
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
