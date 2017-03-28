<template>
    <div class="wf-panel wf-settingpanel">
        <div class="wf-panel-tab">
            <a href="javascript:;" @click="clickTab" data-tabname="component" class="tabitem"
               v-bind:class="[component?'current':'']">控件设置</a>
            <a href="javascript:;" @click="clickTab" data-tabname="form" class="tabitem "
               v-bind:class="[component?'':'current']">审批设置</a>
        </div>
        <formsetting v-show="!component"></formsetting>
        <widgetsettings v-show="component"></widgetsettings>
    </div>

</template>
<script type="text/ecmascript-6">
    import formsetting from "@/components/formsetting"
    import widgetsettings from "@/components/widgetsettings"
    export default{
        name: 'setting',
        data(){
            return {
                component: false
            }
        },
        components: {
            formsetting,
            widgetsettings
        },
        methods: {
            clickTab: function (e) {
                if (e.currentTarget.getAttribute('data-tabName') === 'component') {
                    this.component = true
                } else {
                    this.component = false
                }
            }
        },
        created: function () {
            let self = this
            drag.$on("changeTab", function (bool) {
                self.component = bool
            })
           /* drag.$on("selectComponent", function (obj) {
                self.supportSetting = Object.assign({}, self.supportSetting, obj)
                console.log(self.supportSetting)
            })*/
        }
    }
</script>
