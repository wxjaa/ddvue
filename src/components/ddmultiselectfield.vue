<template>
    <div class="wf-widgetsitem" data-type="ddmultiselectfield" v-on:mousedown="start">
        <label>
            多选框
        </label>
        <i class="widgeticon ddmultiselectfield"></i>
    </div>
</template>
<script>
    export default{
        name: 'ddmultiselectfield',
        data: function () {
            return {
                offsetTop: 0,
                offsetLeft: 0,
                componentView: {
                    name: '多选框',
                    defaultLable: '多选框',
                    defaultProps: '请选择',
                    defaultImportant: false,
                    defaultOptions: [
                        {idx: 1, text: '选项1'},
                        {idx: 2, 'text': '选项2'},
                        {idx: 3, text: '选项3'}
                    ],
                    componentName: 'ddmultiselectfield',
                    supportSetting: ['label', 'placeholder', 'options', 'required', 'important', 'print']
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
