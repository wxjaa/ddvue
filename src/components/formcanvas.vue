<template>
  <div class="wf-formcanvas">
    <div class="wf-formcanvas-title">{{title}}</div>
    <div class="wf-formcanvas-inner">
      <div class="wf-formcanvas-body dropbody" v-bind:class="{empty:isempty}">
        <div class="wf-dragging-mark" v-if="InCanvas"></div>
        <div class="wf-component wf-component-textfield active" >
          <div class="wf-remove icon icon-close" ></div>
          <div class="wf-overlay" ></div>
          <div class="wf-componentview" >
            <div class="wf-componentview-border" ><label
              class="wf-componentview-label" >单行输入框</label><span
              class="wf-componentview-placeholder">请输入</span></div>
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
        InCanvas: false
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

        }
      })
    },
    mounted: function () {
      let dom = document.querySelector('.wf-formcanvas-body')
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
