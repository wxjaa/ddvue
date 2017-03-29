<template>
    <div class="wf-widgetsitem" data-type="dddaterangefield" v-on:mousedown="start">
        <label>
            日期区间
        </label>
        <i class="widgeticon dddaterangefield"></i>
    </div>
</template>
<script>
    export default{
        name: 'dddaterangefield',
        data: function () {
            return {
                offsetTop: 0,
                offsetLeft: 0,
                componentView: {
                    name: '日期区间',
                    defaultLable: '开始时间',
                    defaultLable2: '结束时间',
                    defaultProps: '请选择',
                    defaultProps2: '请选择',
                    defaultImportant: false,
                    defaultAutorekonTime: false,
                    defaultFormat: 'yyyy-MM-dd',
                    defaultSubtitle:'时长',
                    componentName: 'dddaterangefield',
                    supportSetting: [
                        'label',
                        'label2',
                        'placeholder',
                        'placeholder2',
                        'dateformat',
                        'required',
                        'important',
                        'autorekonTime',
                        'subtitle',
                        'print']
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
