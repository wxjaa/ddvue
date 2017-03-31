<template>
    <div class="wf-form wf-formsettings">
        <div class="wf-field wf-setting-title">
            <div class="fieldname">
                <span>审批名称</span>
                <span class="fieldinfo">最多10个字</span>
            </div>
            <div class="fieldblock">
                <input type="text" @input="changeInfo" maxlength="10" v-model="title">
            </div>
        </div>
        <div class="wf-field wf-setting-description">
            <div class="fieldname">
                <span>审批说明</span>
                <span class="fieldinfo">最多100个字</span>
            </div>
            <div class="fieldblock">
                <textarea type="text" @input="changeInfo" maxlength="100" v-model="description"></textarea>
            </div>
        </div>
        <div class="wf-field wf-setting-icon">
            <div class="fieldname">
                图标
            </div>
            <div class="fieldblock">
                <div class="wf-iconselect">
                    <label @click="selectIcon" :data-index="index" :data-icon="item.value" v-for="(item,index) in icons"
                           class="iconitem"
                           v-bind:class="index==selected?'seltected':''">
                        <i class="icon icon-checked" v-if="index==selected"></i>
                        <img :src="item.value">

                    </label>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    export default{
        name: "formsetting",
        data: function () {
            return {
                title: '',
                description: '',
                icons: [
                    {
                        name: "common",
                        value: "//gw.alicdn.com/tps/TB1zXtqOpXXXXa6XXXXXXXXXXXX-102-102.png"
                    },
                    {
                        name: "trip",
                        value: "//gw.alicdn.com/tps/TB1Ez8XOpXXXXa5XpXXXXXXXXXX-102-102.png"
                    }, {
                        name: "out",
                        value: "//gw.alicdn.com/tps/TB1C1XhOpXXXXaKXpXXXXXXXXXX-102-102.png"
                    },
                    {
                        name: "goods",
                        value: "//gw.alicdn.com/tps/TB1tm.TOXXXXXchaXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "biz",
                        value: "//gw.alicdn.com/tps/TB1Y57ZOXXXXXXwaXXXXXXXXXXX-102-102.png"
                    },
                    {
                        name: "leave",
                        value: "//gw.alicdn.com/tps/TB1hcBoOpXXXXbPXXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "message",
                        value: "//gw.alicdn.com/tps/TB1TOZQOXXXXXXVaXXXXXXXXXXX-102-102.png"
                    },
                    {
                        name: "favorite",
                        value: "//gw.alicdn.com/tps/TB1jjpoOpXXXXbHXXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "datacurve",
                        value: "//gw.alicdn.com/tps/TB1.vAMOXXXXXXmaFXXXXXXXXXX-102-102.png"
                    },
                    {
                        name: "timefades",
                        value: "//gw.alicdn.com/tps/TB1UEoTOXXXXXbCaXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "official",
                        value: "//gw.alicdn.com/tps/TB1NA.SOXXXXXbSaXXXXXXXXXXX-102-102.png"
                    },
                    {
                        name: "fly",
                        value: "//gw.alicdn.com/tps/TB12R3NOXXXXXcwaXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "house",
                        value: "//gw.alicdn.com/tps/TB1ESwQOXXXXXbaaXXXXXXXXXXX-102-102.png"
                    },
                    {
                        name: "datapie",
                        value: "//gw.alicdn.com/tps/TB1q5U5OXXXXXXPXVXXXXXXXXXX-102-102.png"
                    }, {
                        name: "tag",
                        value: "//gw.alicdn.com/tps/TB1Pb4eOpXXXXcGXpXXXXXXXXXX-102-102.png"
                    },
                    {
                        name: "love",
                        value: "//gw.alicdn.com/tps/TB1GCw.OXXXXXbOXFXXXXXXXXXX-102-102.png"
                    }, {
                        name: "daily",
                        value: "//gw.alicdn.com/tps/TB1J20kOpXXXXc1XpXXXXXXXXXX-102-102.png"
                    },
                    {
                        name: "weekly",
                        value: "//gw.alicdn.com/tps/TB14v8rOpXXXXXYXpXXXXXXXXXX-102-102.png"
                    }, {
                        name: "monthly",
                        value: "//gw.alicdn.com/tps/TB1NI0nOpXXXXX2XpXXXXXXXXXX-102-102.png"
                    },
                    {
                        name: "promotion",
                        value: "//gw.alicdn.com/tps/TB1Nb.3OXXXXXalaXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "visiting",
                        value: "//gw.alicdn.com/tps/TB1_Y.5OXXXXXcEXVXXXXXXXXXX-102-102.png"
                    }, {
                        name: "behavior",
                        value: "//gw.alicdn.com/tps/TB15DEPOXXXXXXTaFXXXXXXXXXX-102-102.png"
                    }, {
                        name: "warehouse",
                        value: "//gw.alicdn.com/tps/TB13Bw.OXXXXXXQXVXXXXXXXXXX-102-102.png"
                    }, {
                        name: "schoolAttendance",
                        value: "//gw.alicdn.com/tps/TB1zhc.OXXXXXa4XVXXXXXXXXXX-102-102.png"
                    }, {
                        name: "schoolLog",
                        value: "//gw.alicdn.com/tps/TB1i4ldOpXXXXaHXFXXXXXXXXXX-102-102.png"
                    }, {
                        name: "schoolStatement",
                        value: "//gw.alicdn.com/tps/TB1Ons_OXXXXXbpXVXXXXXXXXXX-102-102.png"
                    }, {
                        name: "meeting",
                        value: "//gw.alicdn.com/tps/TB1mZhiOpXXXXccXpXXXXXXXXXX-102-102.png"
                    }, {
                        name: "temporaryNotice",
                        value: "//gw.alicdn.com/tps/TB118RbOpXXXXahXVXXXXXXXXXX-102-102.png"
                    }, {
                        name: "dutyLog",
                        value: "//gw.alicdn.com/tps/TB18D0zOpXXXXXbXXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "propaganda",
                        value: "//gw.alicdn.com/tps/TB1a.VeOpXXXXc1XVXXXXXXXXXX-102-102.png"
                    }, {
                        name: "jobs",
                        value: "//gw.alicdn.com/tps/TB1FXVmOpXXXXbGXFXXXXXXXXXX-102-102.png"
                    }, {
                        name: "recruitment",
                        value: "//gw.alicdn.com/tps/TB1i7lmOpXXXXbvXFXXXXXXXXXX-102-102.png"
                    }, {
                        name: "inchapter",
                        value: "//gw.alicdn.com/tps/TB1HXRxOpXXXXbbXpXXXXXXXXXX-102-102.png"
                    }, {
                        name: "class",
                        value: "//gw.alicdn.com/tps/TB1Tv0GOpXXXXX7XXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "department",
                        value: "//gw.alicdn.com/tps/TB1E2NEOpXXXXaHXXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "conference",
                        value: "//gw.alicdn.com/tps/TB19xFfOpXXXXbBXVXXXXXXXXXX-102-102.png"
                    }, {
                        name: "gas",
                        value: "//gw.alicdn.com/tps/TB13G0EOpXXXXbuXXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "salary",
                        value: "//gw.alicdn.com/tps/TB1QWA7OXXXXXb9aXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "discount",
                        value: "//gw.alicdn.com/tps/TB1_Lw6OXXXXXcCaXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "pay",
                        value: "//gw.alicdn.com/tps/TB1L8xjOpXXXXbYXFXXXXXXXXXX-102-102.png"
                    }, {
                        name: "contract",
                        value: "//gw.alicdn.com/tps/TB1MLxpOpXXXXbeXFXXXXXXXXXX-102-102.png"
                    }, {
                        name: "collection",
                        value: "//gw.alicdn.com/tps/TB1XQdaOpXXXXbwaXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "cashier",
                        value: "//gw.alicdn.com/tps/TB1z4I6OXXXXXX3apXXXXXXXXXX-102-102.png"
                    }, {
                        name: "departure",
                        value: "//gw.alicdn.com/tps/TB19RptOpXXXXXQXFXXXXXXXXXX-102-102.png"
                    }, {
                        name: "courier",
                        value: "//gw.alicdn.com/tps/TB1k6Z0OXXXXXcyapXXXXXXXXXX-102-102.png"
                    }, {
                        name: "procurement",
                        value: "//gw.alicdn.com/tps/TB14X4tOpXXXXX2XFXXXXXXXXXX-102-102.png"
                    }, {
                        name: "attendance_supplementary",
                        value: "//gw.alicdn.com/tps/TB13Rg5OXXXXXcgaXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "positive",
                        value: "//gw.alicdn.com/tps/TB1Rp0eOpXXXXayaXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "work_instructions",
                        value: "//gw.alicdn.com/tps/TB1eMBJOpXXXXXAXXXXXXXXXXXX-102-102.png"
                    }, {
                        name: "repeat_order",
                        value: "//gw.alicdn.com/tps/TB1GxBnOpXXXXcbXFXXXXXXXXXX-102-102.png"
                    }, {
                        name: "follow",
                        value: "//gw.alicdn.com/tps/TB1fJo3OXXXXXa8apXXXXXXXXXX-102-102.png"
                    }, {
                        name: "general_log",
                        value: "//gw.alicdn.com/tps/TB1E9BoOpXXXXcHXFXXXXXXXXXX-102-102.png"
                    }, {
                        name: "business",
                        value: "//gw.alicdn.com/tps/TB13336OXXXXXcGapXXXXXXXXXX-102-102.png"
                    }],
                selected: 0
            }
        },
        methods: {
            selectIcon: function (e) {
                this.selected = e.currentTarget.getAttribute('data-index')
                let obj = {
                    title: this.title,
                    icon: e.currentTarget.getAttribute('data-icon'),
                    description: this.description
                }
                drag.$emit("changeInfo", obj)
            },
            changeInfo: function () {
                let obj = {
                    title: this.title,
                    icon: this.icons[this.selected].value,
                    description: this.description
                }
                drag.$emit("changeInfo", obj)
            }
        }
    }
</script>
