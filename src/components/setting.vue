<template>
    <div class="wf-panel wf-settingpanel">
        <div class="wf-panel-tab">
            <a href="javascript:;" @click="clickTab" data-tabname="component" class="tabitem" v-bind:class="[component?'current':'']">控件设置</a>
            <a href="javascript:;" @click="clickTab" data-tabname="form" class="tabitem " v-bind:class="[component?'':'current']">审批设置</a>
        </div>
        <formsetting></formsetting>
    </div>

</template>
<script>
    import formsetting from "@/components/formsetting"
    export default{
        name:'setting',
        data(){
            return {
                component:false
            }
        },
        components:{
            formsetting
        },
        methods:{
            clickTab: function (e) {
                console.log(e)
            }
        }
    }
</script>