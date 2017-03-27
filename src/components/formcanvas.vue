<template>
    <div class="wf-formcanvas">
        <div class="wf-formcanvas-title">{{title}}</div>
        <div class="wf-formcanvas-inner">
            <div class="wf-formcanvas-body dropbody" v-bind:class="{empty:isempty}">
                <div class="wf-dragging-mark" v-if="InCanvas"></div>

                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='textfield'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-textfield">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-border"><label
                            class="wf-componentview-label">{{item.defaultLable}}</label><span
                            class="wf-componentview-placeholder">{{item.defaultProps}}</span></div>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='textareafield'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-textareafield">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-border"><label
                            class="wf-componentview-label">{{item.defaultLable}}</label><span
                            class="wf-componentview-placeholder">{{item.defaultProps}}</span></div>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='numberfield'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-numberfield">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-border"><label
                            class="wf-componentview-label">{{item.defaultLable}}</label><span
                            class="wf-componentview-placeholder">{{item.defaultProps}}</span></div>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='ddselectfield'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-ddselectfield">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-border"><label
                            class="wf-componentview-label">{{item.defaultLable}}</label><span
                            class="wf-componentview-placeholder">{{item.defaultProps}}</span>
                            <i class="icon icon-enter"></i>
                        </div>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='ddmultiselectfield'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-ddmultiselectfield">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-border"><label
                            class="wf-componentview-label">{{item.defaultLable}}</label><span
                            class="wf-componentview-placeholder">{{item.defaultProps}}</span>
                            <i class="icon icon-enter"></i>
                        </div>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='dddatefield'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-dddatefield">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-border"><label
                            class="wf-componentview-label">{{item.defaultLable}}</label><span
                            class="wf-componentview-placeholder">{{item.defaultProps}}</span>
                            <i class="icon icon-enter"></i>
                        </div>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='dddaterangefield'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-dddaterangefield">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-border" v-for="data in item.getDefaultLabel"><label
                            class="wf-componentview-label">{{data.defaultLable}}</label><span
                            class="wf-componentview-placeholder">{{data.defaultProps}}</span>
                            <i class="icon icon-enter"></i>
                        </div>
                        <span></span>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='ddphotofield'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-ddphotofield">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-border"><label
                            class="wf-componentview-label">{{item.defaultLable}}</label><span
                            class="wf-componentview-placeholder">{{item.defaultProps}}</span>
                            <i class="icon icon-camera"></i>
                        </div>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='tablefield'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-tablefield">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview-area" v-bind:class="{empty:item.components.length<=0}">
                        <span class="emptytip" v-if="item.components.length<=0">可拖入多个组件（不包含明细组件）</span>
                        <div class="wf-componentgroup dropbody">
                            <div class="wf-dragging-mark" v-if="InTableCanvas"></div>
                        </div>
                        <div class="wf-componentview-adddetail">
                            {{item.defaultProps}}
                        </div>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='textnote'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-textnote">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-content">
                            {{item.defaultProps}}
                        </div>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='moneyfield'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-moneyfield">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-border"><label
                            class="wf-componentview-label">{{item.defaultLable}}</label><span
                            class="wf-componentview-placeholder">{{item.defaultProps}}</span>
                        </div>
                        <div class="cnformat">大写：壹万元整（示例）</div>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='ddattachment'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-ddattachment">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-border"><label
                            class="wf-componentview-label">{{item.defaultLable}}</label><span
                            class="wf-componentview-placeholder">{{item.defaultProps}}</span>
                        </div>
                        <i class="icon icon-chakanfujian"></i>
                    </div>
                </div>
                <div v-for="(item,index) in components" v-on:mouseout="mouseOut" v-on:mouseover="hover"
                     v-if="item.componentName=='externalcontactfield'" :data-index="index"
                     v-bind:class="index==selected?'active':''"
                     class="wf-component wf-component-externalcontactfield">
                    <div class="wf-remove icon icon-close" @click="close"></div>
                    <div class="wf-overlay"></div>
                    <div class="wf-componentview">
                        <div class="wf-componentview-border"><label
                            class="wf-componentview-label">{{item.defaultLable}}</label><span
                            class="wf-componentview-placeholder">{{item.defaultProps}}</span>
                        </div>
                        <i class="icon icon-enter"></i>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    export default{
        name: 'formcanvas',
        data: function () {
            return {
                title: '请假',
                isempty: true,
                left: 0,
                top: 0,
                width: 0,
                height: 0,
                InCanvas: false,
                components: [],
                selected: 0,
                InTableCanvas: false
            }
        },
        methods: {
            hover: function (e) {
                e.currentTarget.classList.add('hover')
            },
            mouseOut: function (e) {
                e.currentTarget.classList.remove('hover')
            },
            close: function (e) {
                let dom = e.currentTarget.parentNode;
                let index = dom.getAttribute('data-index');
                this.components.splice(index, 1)
                drag.$emit("changeTab", false)
                if (this.components.length <= 0) {
                    this.isempty = true
                }
            }
        },
        created: function () {
            let self = this
            drag.$on("moveInCanvas", function (obj) {
                if (obj.clientX >= self.left && obj.clientY >= self.top && obj.clientX <= self.left + self.width && obj.clientY <= self.top + self.height) {
                    self.InCanvas = true
                } else {
                    self.InCanvas = false
                }
            })
            drag.$on("moveend", function (obj) {
                if (self.InCanvas) {
                    self.components.push(obj.componentView)
                    self.selected = self.components.indexOf(obj.componentView);
                    drag.$emit('changeTab', true)
                    drag.$emit("selectComponent", obj)
                }
                self.InCanvas = false
                if (self.components.length <= 0) {
                    self.isempty = true
                } else {
                    self.isempty = false
                }
            })
        },
        mounted: function () {
            let dom = document.querySelector('.wf-formcanvas-inner')
            var actualLeft = dom.offsetLeft;
            var current = dom.offsetParent;
            while (current !== null) {
                actualLeft += current.offsetLeft;
                current = current.offsetParent;
            }
            var actualTop = dom.offsetTop;
            var current = dom.offsetParent;
            while (current !== null) {
                actualTop += current.offsetTop;
                current = current.offsetParent;
            }
            this.left = actualLeft
            this.top = actualTop
            this.width = dom.offsetWidth
            this.height = dom.offsetHeight
        },
        updated: function () {
        }
    }
</script>
