<template>
    <div class="wf-formcanvas">
        <div class="wf-formcanvas-title">{{title}}</div>
        <div class="wf-formcanvas-inner">
            <div class="wf-formcanvas-body dropbody" v-bind:class="{empty:isempty}">
                <div class="wf-dragging-mark" v-if="InCanvas==0"></div>

                <div v-for="(item,index) in components">
                    <div v-if="item.componentName=='textareafield'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-textareafield">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span></span></div>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='textfield'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-textfield">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span></span></div>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='numberfield'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-numberfield">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span></span></div>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='ddselectfield'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseover="hover"
                             v-on:mouseout="mouseOut"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-ddselectfield">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span></span>
                                    <i class="icon icon-enter"></i>
                                </div>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='ddmultiselectfield'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-ddmultiselectfield">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span></span>
                                    <i class="icon icon-enter"></i>
                                </div>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='dddatefield'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-dddatefield">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span></span>
                                    <i class="icon icon-enter"></i>
                                </div>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='dddaterangefield'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-dddaterangefield">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span></span>
                                    <i class="icon icon-enter"></i>
                                </div>
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable2}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps2}}<span
                                    v-if="item.defaultImportant">（必填）</span></span>
                                    <i class="icon icon-enter"></i>
                                </div>
                                <div class="wf-componentview-border" v-if="item.defaultAutorekonTime"><label
                                    class="wf-componentview-label"><span>{{item.defaultSubtitle}}</span><span
                                >（天）</span></label><span
                                    class="wf-componentview-placeholder"></span></div>
                                <span></span>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='ddphotofield'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-ddphotofield">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span></span>
                                    <i class="icon icon-camera"></i>
                                </div>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='tablefield'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-tablefield">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <label class="wf-componentview-label">明细</label>
                                <div class="wf-componentview-area" v-bind:class="{empty:item.components.length<=0}">
                                    <span class="emptytip" v-if="item.components.length<=0">可拖入多个组件（不包含明细组件）</span>
                                    <div class="wf-componentgroup dropbody">
                                        <div class="wf-dragging-mark" v-if="item.InTableCanvas==0"></div>
                                        <div v-for="(itemInTable,idx) in item.components">
                                            <div v-if="itemInTable.componentName=='textareafield'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseout="mouseOut"
                                                     v-on:mouseover="hover"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-textareafield">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps}}<span
                                                            v-if="item.defaultImportant">（必填）</span></span></div>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                            <div v-if="itemInTable.componentName=='textfield'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseout="mouseOut"
                                                     v-on:mouseover="hover"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-textfield">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span></span></div>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                            <div v-if="itemInTable.componentName=='numberfield'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseout="mouseOut"
                                                     v-on:mouseover="hover"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-numberfield">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span></span></div>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                            <div v-if="itemInTable.componentName=='ddselectfield'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseover="hover"
                                                     v-on:mouseout="mouseOut"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-ddselectfield">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span></span>
                                                            <i class="icon icon-enter"></i>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                            <div v-if="itemInTable.componentName=='ddmultiselectfield'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseout="mouseOut"
                                                     v-on:mouseover="hover"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-ddmultiselectfield">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span></span>
                                                            <i class="icon icon-enter"></i>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                            <div v-if="itemInTable.componentName=='dddatefield'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseout="mouseOut"
                                                     v-on:mouseover="hover"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-dddatefield">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span></span>
                                                            <i class="icon icon-enter"></i>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                            <div v-if="itemInTable.componentName=='dddaterangefield'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseout="mouseOut"
                                                     v-on:mouseover="hover"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-dddaterangefield">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span></span>
                                                            <i class="icon icon-enter"></i>
                                                        </div>
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable2}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps2}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span></span>
                                                            <i class="icon icon-enter"></i>
                                                        </div>
                                                        <div class="wf-componentview-border"
                                                             v-if="itemInTable.defaultAutorekonTime"><label
                                                            class="wf-componentview-label"><span>{{itemInTable.defaultSubtitle}}</span><span
                                                        >（天）</span></label><span
                                                            class="wf-componentview-placeholder"></span></div>
                                                        <span></span>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                            <div v-if="itemInTable.componentName=='ddphotofield'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseout="mouseOut"
                                                     v-on:mouseover="hover"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-ddphotofield">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span></span>
                                                            <i class="icon icon-camera"></i>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                            <div v-if="itemInTable.componentName=='textnote'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseout="mouseOut"
                                                     v-on:mouseover="hover"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-textnote">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-content">
                                                            {{item.defaultProps}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                            <div v-if="itemInTable.componentName=='moneyfield'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseout="mouseOut"
                                                     v-on:mouseover="hover"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-moneyfield">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span></span>
                                                        </div>
                                                        <div class="cnformat" v-if="itemInTable.defaultTranslate">
                                                            大写：壹万元整（示例）
                                                        </div>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                            <div v-if="itemInTable.componentName=='ddattachment'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseout="mouseOut"
                                                     v-on:mouseover="hover"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-ddattachment">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span></span>
                                                        </div>
                                                        <i class="icon icon-chakanfujian"></i>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                            <div v-if="itemInTable.componentName=='externalcontactfield'">
                                                <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                                                     v-on:mouseout="mouseOut"
                                                     v-on:mouseover="hover"
                                                     :data-index="idx"
                                                     v-bind:class="idx==item.selected?'active':''"
                                                     class="wf-component wf-component-externalcontactfield">
                                                    <div class="wf-remove icon icon-close" @click="close"></div>
                                                    <div class="wf-overlay"></div>
                                                    <div class="wf-componentview">
                                                        <div class="wf-componentview-border"><label
                                                            class="wf-componentview-label">{{itemInTable.defaultLable}}</label><span
                                                            class="wf-componentview-placeholder">{{itemInTable.defaultProps}}<span
                                                            v-if="itemInTable.defaultImportant">（必填）</span></span>
                                                        </div>
                                                        <i class="icon icon-enter"></i>
                                                    </div>
                                                </div>
                                                <div class="wf-dragging-mark" v-if="item.InTableCanvas==idx+1"></div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                                <div class="wf-componentview-adddetail">
                                    {{item.defaultAction}}
                                </div>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='textnote'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-textnote">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-content">
                                    {{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span>
                                </div>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='moneyfield'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-moneyfield">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span></span>
                                </div>
                                <div class="cnformat" v-if="item.defaultTranslate">大写：壹万元整（示例）</div>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='ddattachment'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-ddattachment">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span></span>
                                </div>
                                <i class="icon icon-chakanfujian"></i>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                    <div v-if="item.componentName=='externalcontactfield'">
                        <div @mousedown="mouseDown" draggable="true" v-on:dragstart="movestart"
                             v-on:mouseout="mouseOut"
                             v-on:mouseover="hover"
                             :data-index="index"
                             v-bind:class="index==selected?'active':''"
                             class="wf-component wf-component-externalcontactfield">
                            <div class="wf-remove icon icon-close" @click="close"></div>
                            <div class="wf-overlay"></div>
                            <div class="wf-componentview">
                                <div class="wf-componentview-border"><label
                                    class="wf-componentview-label">{{item.defaultLable}}</label><span
                                    class="wf-componentview-placeholder">{{item.defaultProps}}<span
                                    v-if="item.defaultImportant">（必填）</span></span>
                                </div>
                                <i class="icon icon-enter"></i>
                            </div>
                        </div>
                        <div class="wf-dragging-mark" v-if="InCanvas==index+1"></div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    //  import draggable from 'vuedraggable'
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
                InCanvas: null,
                components: [],
                selected: null,
                InTableCanvas: false,
                domArr: [],
                isDrag: false,
                dragIndex: null,
                tabIndex: null
            }
        },
        /* components: {
         draggable
         },*/
        methods: {
            hover: function (e) {
                e.currentTarget.classList.add('hover')
            },
            mouseOut: function (e) {
                e.currentTarget.classList.remove('hover')
            },
            close: function (e) {
                e.preventDefault();
                e.stopPropagation();
                let dom = e.currentTarget.parentNode;
                let index = dom.getAttribute('data-index');
                this.components.splice(index, 1)
                if (dom.className.indexOf('active') > 0) {
                    drag.$emit("changeTab", false)
                    this.selected = null;
                }
                if (this.components.length <= 0) {
                    this.isempty = true
                }
            },
            mouseDown: function (e) {
                let dom = e.currentTarget;
                let index = dom.getAttribute('data-index');
                let obj = this.components[index]
                if (this.selected !== index) {
                    this.selected = index
                    drag.$emit("selectComponent", obj)
                    drag.$emit('changeTab', true)
                }
            },
            movestart: function (e) {
                let obj = {}
                let dom = e.currentTarget
                dom.classList.add('draging')
                let index = dom.getAttribute('data-index');
                let actualLeft = dom.offsetLeft;
                let current = dom.offsetParent;
                while (current !== null) {
                    actualLeft += current.offsetLeft;
                    current = current.offsetParent;
                }
                let actualTop = dom.offsetTop;
                while (current !== null) {
                    actualTop += current.offsetTop;
                    current = current.offsetParent;
                }
                obj.componentName = this.components[index].componentName;
                obj.componentText = this.components[index].name;
                obj.clientX = e.clientX;
                obj.clientY = e.clientY;
                obj.isstart = true;
                obj.componentView = this.components[index];
                this.isDrag = true;
                this.dragIndex = index;
                drag.$emit("movestart", obj)
            },
            queryDomByIndex: function (index) {
                let dom = document.querySelectorAll('.wf-component')
                for (let i = 0, l = dom.length; i < l; i++) {
                    let obj = dom[i];
                    if (obj.getAttribute('data-index') == index) {
                        return obj
                    }
                }
            }
        },
        created: function () {
            let self = this
            drag.$on("moveInCanvas", function (obj) {
                //当鼠标在中间可拖动区域
                if (obj.clientX >= self.left && obj.clientY >= self.top && obj.clientX <= self.left + self.width && obj.clientY <= self.top + self.height) {
                    //鼠标距离可拖动区域顶部的距离
                    let topInCanvas = obj.clientY - self.top;
                    if (self.domArr.length <= 0) {
                        self.InCanvas = 0;
                        self.tabIndex = null;
                    } else if (self.domArr.length === 1) {
                        if (topInCanvas <= self.domArr[0].middle_top) {
                            self.InCanvas = 0;
                            self.tabIndex = null;
                        } else if (topInCanvas > self.domArr[0].middle_lower) {
                            self.InCanvas = 1;
                            self.tabIndex = null;
                        } else if (topInCanvas <= self.domArr[0].middle_lower && topInCanvas > self.domArr[0].middle_top) {
                            let item = self.domArr[0];
                            self.InCanvas = null;
                            self.tabIndex = 0;
                            if (item.domArr.length <= 0) {
                                self.components[0].InTableCanvas = 0
                            } else if (topInCanvas > item.domArr[item.domArr.length - 1].middle_lower) {
                                self.components[0].InTableCanvas = item.domArr.length
                            } else if (item.domArr.length > 1) {
                                for (let m = 0, n = item.domArr.length - 1; m < n; m++) {
                                    if (topInCanvas > item.domArr[m].middle_lower && topInCanvas <= item.domArr[m + 1].middle_top) {
                                        self.components[0].InTableCanvas = m + 1
                                    }
                                }
                            }
                        }
                    } else
                    //中间已有组件数量大于1
                    {
                        if (topInCanvas <= self.domArr[0].middle_top) {
                            self.InCanvas = 0;
                            self.tabIndex = null;
                        } else if (topInCanvas > self.domArr[self.domArr.length - 1].middle_lower) {
                            self.InCanvas = self.domArr.length;
                            self.tabIndex = null;
                        }
                        else {
                            for (let i = 0, l = self.domArr.length; i < l - 1; i++) {
                                let item = self.domArr[i];
                                let nextItem = self.domArr[i + 1];
                                //在明细组件里面
                                if (topInCanvas > item.middle_top && topInCanvas <= item.middle_lower) {
                                    self.InCanvas = null;
                                    self.tabIndex = i;
                                    if (item.domArr.length <= 0) {
                                        self.components[i].InTableCanvas = 0
                                    } else if (topInCanvas > item.domArr[item.domArr.length - 1].middle_lower) {
                                        self.components[i].InTableCanvas = item.domArr.length
                                    } else {
                                        for (let m = 0, n = item.domArr.length - 1; m < n; m++) {
                                            if (topInCanvas > item.domArr[m].middle_lower && topInCanvas <= item.domArr[m + 1].middle_top) {
                                                self.components[i].InTableCanvas = m + 1
                                            }
                                        }
                                    }
                                } else if (topInCanvas > item.middle_lower && topInCanvas <= nextItem.middle_top) {
                                    self.InCanvas = i + 1;
                                    self.tabIndex = null;
                                    self.components[i].InTableCanvas = null
                                }

                            }
                        }
                    }

                    if (self.tabIndex != null) {
                        self.InCanvas = null
                    } else {
                        self.InCanvas = self.InCanvas || 0
                    }
                    if (self.InCanvas != null) {
                        for (let i = 0, l = self.components.length; i < l; i++) {
                            self.components[i].InTableCanvas = null
                        }
                    }
                } else {
                    self.InCanvas = null;
                    for (let i = 0, l = self.components.length; i < l; i++) {
                        self.components[i].InTableCanvas = null
                    }
                }
            })
            drag.$on("moveend", function (obj) {
                let component = JSON.stringify(obj);
                component = JSON.parse(component);
                drag.$emit("dragend", obj);
                if (self.InCanvas !== null) {
                    //拖动现在已有组件
                    if (self.isDrag) {
                        self.dragIndex = self.dragIndex >> 0;
                        if (self.dragIndex != self.InCanvas - 1 && self.dragIndex != self.InCanvas) {
                            let dragItem = self.components[self.dragIndex];
                            self.components.splice(self.dragIndex, 1);
                            self.components.splice(self.InCanvas, 0, dragItem);
                            self.selected = self.components.indexOf(dragItem);
                        } else {
                            let dom = self.queryDomByIndex(self.dragIndex);
                            dom.classList.remove('draging');
                        }
                        self.dragIndex = null;
                        self.isDrag = false;
                    } else {
                        //添加新组件
                        let idx = 0;
                        for (let i = 0; i < self.components.length; i++) {
                            let item = self.components[i];
                            if (item.name == component.componentView.name) {
                                idx++;
                            }
                        }
                        component.componentView.idx = self.components.length;
                        if (idx > 0) {
                            component.componentView.defaultLable = component.componentView.defaultLable + "（" + idx + "）";
                        }
                        if (self.InCanvas > 0) {
                            self.components.splice(self.InCanvas, 0, component.componentView);
                        } else if (self.InCanvas == 0) {
                            self.components.unshift(component.componentView);
                        }
                        self.selected = self.components.indexOf(component.componentView);
                        drag.$emit('changeTab', true);
                        drag.$emit("selectComponent", component.componentView)
                    }
                    self.InCanvas = null;
                } else {

                    //添加新组件
                    let idx = 0;
                    for (let i = 0; i < self.components[self.tabIndex].components.length; i++) {
                        let item = self.components[self.tabIndex].components[i];
                        if (item.name == component.componentView.name) {
                            idx++;
                        }
                    }
                    component.componentView.idx =  self.components[self.tabIndex].components.length;
                    if (idx > 0) {
                        component.componentView.defaultLable = component.componentView.defaultLable + "（" + idx + "）";
                    }
                    if (self.components.InTableCanvas > 0) {
                        self.components[self.tabIndex].components.splice(self.tabIndex, 0, component.componentView);
                    } else if (self.components.InTableCanvas == 0) {
                        self.components[self.tabIndex].components.unshift(component.componentView);
                    }
                    //self.selected = self.components.indexOf(component.componentView);
                    for (let i = 0, l = self.components.length; i < l; i++) {
                        self.components[i].InTableCanvas = null;
                    }
                    drag.$emit('changeTab', true);
                    drag.$emit("selectComponent", component.componentView)
                }
                if (self.components.length <= 0) {
                    self.isempty = true
                } else {
                    self.isempty = false
                }
            })
            drag.$on("changeComponent", function (obj) {
                for (let i = 0; i < self.components.length; i++) {
                    let item = self.components[i];
                    if (item.idx == obj.idx) {
                        self.components.splice(i, 1, obj)

                    }
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
            this.domArr = []
            let domArr = document.querySelectorAll('.wf-component')
            for (let i = 0, l = domArr.length; i < l; i++) {
                let obj = domArr[i];
                if (obj.className.indexOf('wf-component-tablefield') >= 0) {
                    let middleDomArr = [];
                    let objTop = obj.offsetTop;
                    let middleDom = obj.querySelectorAll('.wf-component')
                    for (let m = 0, n = middleDom.length; m < n; m++) {
                        let item = middleDom[m];
                        middleDomArr.push({
                            height: item.offsetHeight,
                            middle: (item.offsetTop + item.offsetHeight / 2) >> 0,
                            top: item.offsetTop + objTop
                        })
                    }
                    this.domArr.push({
                        height: obj.offsetHeight,
                        middle_top: (obj.offsetTop + 18) >> 0,
                        middle_lower: (obj.offsetTop + obj.offsetHeight - 23) >> 0,
                        top: objTop,
                        domArr: middleDomArr
                    })
                } else {
                    this.domArr.push({
                        height: obj.offsetHeight,
                        middle_top: (obj.offsetTop + obj.offsetHeight / 2) >> 0,
                        middle_lower: (obj.offsetTop + obj.offsetHeight / 2) >> 0,
                        top: obj.offsetTop
                    })
                }

            }
        }
    }
</script>
