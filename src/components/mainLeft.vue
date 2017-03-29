<template>
    <div class="wf-panel wf-widgetspanel">
        <div class="wf-panel-tab">
            <a href="javascript:;" class="tabitem current">控件</a>
        </div>
        <div class="wf-panel-body">
            <textfield></textfield>
            <textareafield></textareafield>
            <numberfield></numberfield>
            <ddselectfield></ddselectfield>
            <ddmultiselectfield></ddmultiselectfield>
            <dddatefield></dddatefield>
            <dddaterangefield></dddaterangefield>

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
            return {}
        },
        components:{
            textfield,
            textareafield,
            numberfield,
            ddselectfield,
            ddmultiselectfield,
            dddatefield,
            dddaterangefield
        }
    }
</script>
