<template>
    <div class="wf-header">
        <div class="head-title">
            <a href="javascript:;">
                <img class="navbar-logo" src="//gtms01.alicdn.com/tps/i1/TB17dLlLXXXXXXAXVXX4e0PNFXX-336-78.png"
                     alt="返回审批管理" data-reactid=".0.0.0.0.0">
                <span class="navbar-head">设计器</span>
            </a>
        </div>
        <headactions></headactions>
    </div>
</template>
<script type="text/ecmascript-6">
    import headactions from "@/components/headActions"
    export default{
        name: 'header',
        data(){
            return {}
        },
        components:{
            headactions
        }
    }
</script>
