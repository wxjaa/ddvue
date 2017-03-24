<template>
    <div class="head-actions" v-bind:class="{disabled:isdisable}">
        <button class="wf-button wf-button-green">预览</button>
        <button class="wf-button wf-button-cyan">保存</button>
        <button class="wf-button wf-button-blue">保存并启用</button>
    </div>
</template>
<script>
    export default{
        name: "head-actions",
        data(){
            return {}
        }
    }
</script>