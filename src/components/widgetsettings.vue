<template>
    <div class="wf-form wf-widgetsettings">
        <div v-if="supportSetting.label" class="wf-field wf-setting-label">
            <div class="fieldname">
                <span>标题</span>
                <span class="fieldinfo">最多10个字</span>
            </div>
            <div class="fieldblock">
                <input type="text" @input="changeComponent" v-model="supportSetting.defaultLable">
            </div>
        </div>
        <div v-if="supportSetting.placeholder" class="wf-field wf-setting-placeholder">
            <div class="fieldname">
                <span>提示文字</span>
                <span class="fieldinfo">最多20个字</span>
            </div>
            <div class="fieldblock">
                <input type="text" @input="changeComponent" v-model="supportSetting.defaultProps">
            </div>
        </div>
        <div v-if="supportSetting.uint" class="wf-field wf-setting-placeholder">
            <div class="fieldname">
                <span>单位</span>
                <span class="fieldinfo">最多20个字</span>
            </div>
            <div class="fieldblock">
                <input type="text" @input="changeComponent" v-model="supportSetting.defaulUint">
            </div>
        </div>
        <div v-if="supportSetting.options" class="wf-field wf-setting-options">
            <div class="fieldname">
                <span>选项</span>
                <span class="fieldinfo">最多200项,每项最多20个字</span>
            </div>
            <div v-bind:class="{limitdel:options<=1,limitadd:options>=200}">
                <div v-for="n in options" class="fieldblock wf-setting-options">
                    <input type="text" maxlength="20" :value="'选项'+n">
                    <a href="javascript:void(0);" @click="del" class="action action-del">
                        <i class="icon icon-minus"></i>
                    </a>
                    <a href="javascript:void(0);" v-on:click="add" class="action action-add">
                        <i class="icon icon-plus"></i>
                    </a>
                </div>
                <!-- <div class="fieldblock wf-setting-options">
                     <input type="text" maxlength="20" value="选项1">
                     <a href="javascript:;" class="action action-del">
                         <i class="icon icon-minus"></i>
                     </a>
                     <a href="javascript:;" class="action action-add">
                         <i class="icon icon-plus"></i>
                     </a>
                 </div>
                 <div class="fieldblock wf-setting-options">
                     <input type="text" maxlength="20" value="选项1">
                     <a href="javascript:;" class="action action-del">
                         <i class="icon icon-minus"></i>
                     </a>
                     <a href="javascript:;" class="action action-add">
                         <i class="icon icon-plus"></i>
                     </a>
                 </div>-->
            </div>
        </div>

        <div v-if="supportSetting.important" class="wf-field wf-setting-required">
            <div class="fieldname">验证</div>
            <label class="fieldblock">
                <input type="checkbox" @change="changeComponent" value="1"
                       v-model="supportSetting.defaultImportant">
                <span class="verticalmiddle">必填</span>
            </label>

        </div>

        <div v-if="supportSetting.print" class="wf-field wf-setting-print">
            <div class="fieldname">打印</div>
            <label class="fieldblock">
                <input type="checkbox" value="1" checked>
                <span class="verticalmiddle">参与打印</span>
                <span class="verticalmiddle">（如不勾选打印时，不显示此项）</span>
            </label>
        </div>
    </div>
</template>
<script>
    export default{
        data: function () {
            return {
                options: 3,
                supportSetting: {}
            }
        },
        methods: {
            add: function (e) {
                this.options++
            },
            del: function () {
                this.options--;
            }
        },
        methods: {
            changeComponent: function () {
                console.log(this.supportSetting)
                drag.$emit("changeComponent",this.supportSetting);
            }
        },
        created: function () {
            let self = this
            drag.$on("selectComponent", function (obj) {
                for (let i = 0; i < obj.supportSetting.length; i++) {
                    self.supportSetting[obj.supportSetting[i]] = true
                }
                self.supportSetting = Object.assign({}, self.supportSetting, obj)
            })
        },
        updated: function () {
        }
    }
</script>
