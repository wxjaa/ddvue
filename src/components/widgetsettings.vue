<template>
    <div class="wf-form wf-widgetsettings">
        <div v-if="supportSetting.label" class="wf-field wf-setting-label">
            <div class="fieldname">
                <span>标题</span>
                <span class="fieldinfo">最多10个字</span>
            </div>
            <div class="fieldblock">
                <input type="text" @input="changeComponent" maxlength="10" v-model="supportSetting.defaultLable">
            </div>
        </div>
        <div v-if="supportSetting.label2" class="wf-field wf-setting-label">
            <div class="fieldname">
                <span>标题2</span>
                <span class="fieldinfo">最多10个字</span>
            </div>
            <div class="fieldblock">
                <input type="text" @input="changeComponent" maxlength="10" v-model="supportSetting.defaultLable2">
            </div>
        </div>
        <div v-if="supportSetting.placeholder" class="wf-field wf-setting-placeholder">
            <div class="fieldname">
                <span>提示文字</span>
                <span class="fieldinfo">最多20个字</span>
            </div>
            <div class="fieldblock">
                <input type="text" @input="changeComponent" maxlength="20" v-model="supportSetting.defaultProps">
            </div>
        </div>
        <div v-if="supportSetting.placeholder2" class="wf-field wf-setting-placeholder">
            <div class="fieldname">
                <span>提示文字</span>
                <span class="fieldinfo">最多20个字</span>
            </div>
            <div class="fieldblock">
                <input type="text" @input="changeComponent" maxlength="20" v-model="supportSetting.defaultProps2">
            </div>
        </div>
        <div v-if="supportSetting.dateformat" class="wf-field wf-setting-placeholder">
            <div class="fieldname">
                <span>日期类型</span>
            </div>
            <div class="fieldname">
                <label class="fieldblock">
                    <input type="radio" name="dateformat" v-model="supportSetting.defaultFormat"
                           value="yyyy-MM-dd HH:mm">
                    <span class="verticalmiddle">年-月-日 时:分</span>
                </label>
                <label class="fieldblock">
                    <input type="radio" name="dateformat" v-model="supportSetting.defaultFormat" value="yyyy-MM-dd">
                    <span class="verticalmiddle">年-月-日</span>
                </label>
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
        <div v-if="supportSetting.defaultOptions" class="wf-field wf-setting-options">
            <div class="fieldname">
                <span>选项</span>
                <span class="fieldinfo">最多200项,每项最多20个字</span>
            </div>
            <div
                v-bind:class="{limitdel:supportSetting.defaultOptions.length<=1,limitadd:supportSetting.defaultOptions.length>=200}">
                <div v-for="(n,index) in supportSetting.defaultOptions" class="fieldblock wf-setting-options">
                    <input type="text" maxlength="20" v-model="n.text">
                    <a @click="del" v-bind:data-index="index" class="action action-del">
                        <i class="icon icon-minus"></i>
                    </a>
                    <a @click="add" v-bind:data-index="index" class="action action-add">
                        <i class="icon icon-plus"></i>
                    </a>
                </div>
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
        <div v-if="supportSetting.autorekonTime" class="wf-field-group">
            <div class="wf-field">
                <div class="fieldname">自动计算时长</div>
            </div>
            <div class="wf-field wf-setting-duration">
                <label class="fieldblock">
                    <input type="checkbox" @change="changeComponent" value="1"
                           v-model="supportSetting.defaultAutorekonTime">
                    <span class="verticalmiddle">开启</span>
                </label>
            </div>
            <div class="wf-setting-duration-label" v-if="supportSetting.defaultAutorekonTime">
                <div class="wf-field wf-setting-label">
                    <div class="fieldname">
                        <span>标题</span>
                        <span class="fieldinfo">最多10个字</span>
                    </div>
                    <div class="fieldblock">
                        <input type="text" maxlength="10" v-model="supportSetting.defaultSubtitle">
                    </div>
                </div>
            </div>

        </div>
        <div v-if="supportSetting.sync" class="wf-field wf-setting-required">
            <div class="fieldname">同步到考勤</div>
            <label class="fieldblock">
                <input type="checkbox" @change="changeComponent" value="1"
                       v-model="supportSetting.defaultSync">
                <span class="verticalmiddle">开启</span>
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
                supportSetting: {}
            }
        },
        methods: {
            add: function (e) {
                e.stopPropagation()
                e.preventDefault()
                let index = e.currentTarget.getAttribute('data-index');
                for (let i = 0, l = this.supportSetting.defaultOptions.length; i < l; i++) {
                    let has = false;
                    for (let item in this.supportSetting.defaultOptions) {
                        if (this.supportSetting.defaultOptions[item].idx == (i + 1)) {
                            has = true
                        }
                    }
                    if (!has) {
                        this.supportSetting.defaultOptions.splice((+index + 1), 0, {idx: i + 1, text: '选项' + (i + 1)})
                        return
                    }
                }
                if (index == this.supportSetting.defaultOptions.length - 1) {
                    this.supportSetting.defaultOptions.push({
                        idx: (this.supportSetting.defaultOptions.length + 1),
                        text: '选项' + (this.supportSetting.defaultOptions.length + 1)
                    })
                } else {
                    this.supportSetting.defaultOptions.splice((+index + 1), 0, {
                        idx: (this.supportSetting.defaultOptions.length + 1),
                        text: '选项' + (this.supportSetting.defaultOptions.length + 1)
                    })
                }
            },
            del: function (e) {
                e.stopPropagation()
                e.preventDefault()
                let index = e.currentTarget.getAttribute('data-index');
                this.supportSetting.defaultOptions.splice(index, 1)
            },
            changeComponent: function () {
                drag.$emit("changeComponent", this.supportSetting);
            }
        },

        created: function () {
            let self = this
            drag.$on("selectComponent", function (obj) {
                console.log(obj)
                self.supportSetting = {}
                for (let i = 0; i < obj.supportSetting.length; i++) {
                    self.supportSetting[obj.supportSetting[i]] = true
                }
                self.supportSetting = Object.assign({}, self.supportSetting, obj)
                console.log(self.supportSetting)
            })
        },
        updated: function () {
        }
    }
</script>
