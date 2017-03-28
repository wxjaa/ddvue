<template>
    <div class="wf-panel wf-widgetspanel">
        <div class="wf-panel-tab">
            <a href="javascript:;" class="tabitem current">控件</a>
        </div>
        <div class="wf-panel-body">
            <textfield></textfield>
            <textareafield></textareafield>

        </div>
    </div>
</template>
<script type="text/ecmascript-6">
    import textfield from "@/components/textfield"
    import textareafield from "@/components/textareafield"
    export default {
        name: 'mainleft',
        data(){
            return {}
        },
        components:{
            textfield,
            textareafield
        }
    }
</script>
