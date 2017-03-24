<template>
    <div class="wf-formcanvas">
        <div class="wf-formcanvas-title">{{title}}</div>
        <div class="wf-formcanvas-inner">
            <div class="wf-formcanvas-body dropbody" v-bind:class="{empty:isempty}">

            </div>
        </div>
    </div>
</template>
<script>
    export default{
        name:'formcanvas',
        data(){
            return {
                title:'请假',
                isempty:true
            }
        }
    }
</script>