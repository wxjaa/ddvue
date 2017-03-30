<template>
    <div class="wf-panel wf-widgetspanel">
        <div class="wf-panel-tab">
            <a href="javascript:;" class="tabitem current">控件</a>
        </div>
        <div class="wf-panel-body">
            <div v-for="(item,index) in components"
                 class="wf-widgetsitem" v-bind:data-index="index" v-bind:data-type="item.componentName"
                 v-on:mousedown="start">
                <label>
                    {{item.name}}
                </label>
                <i class="widgeticon" v-bind:class="item.componentName"></i>
            </div>

        </div>
    </div>
    </div>
</template>
<script type="text/ecmascript-6">
    import textfield from "@/components/textfield"
    import textareafield from "@/components/textareafield"
    import numberfield from "@/components/numberfield"
    import ddselectfield from "@/components/ddselectfield"
    import ddmultiselectfield from "@/components/ddmultiselectfield"
    import dddatefield from "@/components/dddatefield"
    import dddaterangefield from "@/components/dddaterangefield"
    export default {
        name: 'mainleft',
        data(){
            return {
                components: [
                    {
                        name: '单行输入框',
                        defaultLable: '单行输入框',
                        defaultProps: '请输入',
                        defaultImportant: false,
                        componentName: 'textfield',
                        supportSetting: ['label', 'placeholder', 'required', 'important', 'print']
                    },
                    {
                        name: '多行输入框',
                        defaultLable: '多行输入框',
                        defaultProps: '请输入',
                        defaultImportant: false,
                        componentName: 'textareafield',
                        supportSetting: ['label', 'placeholder', 'required', 'important', 'print']
                    },
                    {
                        name: '数字输入框',
                        defaultLable: '数字输入框',
                        defaultProps: '请输入',
                        defaultImportant: false,
                        componentName: 'numberfield',
                        supportSetting: ['label', 'placeholder', 'required', 'important', 'print', 'uint']
                    },
                    {
                        name: '单选框',
                        defaultLable: '单选框',
                        defaultProps: '请选择',
                        defaultImportant: false,
                        defaultSync: false,
                        defaultOptions: [
                            {idx: 1, text: '选项1'},
                            {idx: 2, 'text': '选项2'},
                            {idx: 3, text: '选项3'}
                        ],
                        componentName: 'ddselectfield',
                        supportSetting: ['label', 'placeholder', 'options', 'sync', 'required', 'important', 'print']
                    },
                    {
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
                    },
                    {
                        name: '日期',
                        defaultLable: '日期',
                        defaultProps: '请选择',
                        defaultImportant: false,
                        defaultFormat: 'yyyy-MM-dd',
                        componentName: 'dddatefield',
                        supportSetting: ['label', 'placeholder', 'dateformat', 'required', 'important', 'print']
                    },
                    {
                        name: '日期区间',
                        defaultLable: '开始时间',
                        defaultLable2: '结束时间',
                        defaultProps: '请选择',
                        defaultProps2: '请选择',
                        defaultImportant: false,
                        defaultAutorekonTime: false,
                        defaultFormat: 'yyyy-MM-dd',
                        defaultSubtitle: '时长',
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
                    },
                    {
                        name: '图片',
                        defaultLable: '图片',
                        defaultImportant: false,
                        componentName: 'ddphotofield',
                        supportSetting: ['label', 'required', 'important', 'print']
                    },
                    {
                        name: '明细',
                        defaultLable: '明细',
                        defaultAction: '增加明细',
                        components: [],
                        componentName: 'tablefield',
                        supportSetting: ['label', 'action', 'required']
                    },
                    {
                        name: '说明文字',
                        defaultLable: '说明文字',
                        defaultImportant: false,
                        defaultProps: '请输入说明文字',
                        defaultShow: false,
                        defaultHref: '',
                        componentName: 'textnote',
                        supportSetting: ['textnote', 'required', 'href', 'print', 'show', 'important']
                    },
                    {
                        name: '金额',
                        defaultLable: '金额（元）',
                        defaultProps: '请输入',
                        defaultImportant: false,
                        defaultTranslate: false,
                        componentName: 'moneyfield',
                        supportSetting: ['label', 'placeholder', 'translate', 'required', 'important', 'print']
                    },
                    {
                        name: '附件',
                        defaultLable: '附件',
                        defaultImportant: false,
                        componentName: 'ddattachment',
                        supportSetting: ['label', 'required', 'important', 'print']
                    },
                    {
                        name: '外部联系人',
                        defaultLable: '外部联系人',
                        defaultProps: '请选择',
                        defaultImportant: false,
                        componentName: 'externalcontactfield',
                        supportSetting: ['label', 'placeholder', 'required', 'important', 'print']
                    }
                ]
            }
        },
        methods: {
            start: function (e) {
                let obj = {}
                let dom = e.currentTarget
                let index = dom.getAttribute('data-index')
                let actualLeft = dom.offsetLeft;
                let current = dom.offsetParent;
                let actualTop = dom.offsetTop;
                while (current !== null) {
                    actualLeft += current.offsetLeft;
                    actualTop += current.offsetTop;
                    current = current.offsetParent;
                }
                obj.componentName = dom.getAttribute("data-type")
                obj.componentText = dom.querySelector('label').innerText
                obj.clientX = e.clientX
                obj.clientY = e.clientY
                obj.isstart = true
                obj.componentView = this.components[index]
                console.log(obj)
                drag.$emit("movestart", obj)
            }
        }
    }
</script>
