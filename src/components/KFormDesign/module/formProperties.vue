<template>
  <div class="properties-centent kk-checkbox" ref="propertiesCentent">
    <a-form>
      <a-form-item v-if="typeof config.layout !== 'undefined'" label="表单布局">
        <a-radio-group buttonStyle="solid" v-model="config.layout">
          <a-radio-button value="horizontal">水平</a-radio-button>
          <a-radio-button value="vertical">垂直</a-radio-button>
          <a-radio-button value="inline">行内</a-radio-button>
        </a-radio-group>
      </a-form-item>
      <a-form-item label="labelCol（水平布局生效）">
        <div class="change-col-box">
          <div>
            <label>span:</label>
            <a-input-number v-model="config.labelCol.span" />
          </div>
        </div>
      </a-form-item>
      <a-form-item label="wrapperCol（水平布局生效）">
        <div class="change-col-box">
          <div>
            <label>span:</label>
            <a-input-number v-model="config.wrapperCol.span" />
          </div>
        </div>
      </a-form-item>
      <a-form-item label="预览模态框宽度">
        <a-input-number style="width:100%;" v-model="previewOptions.width" />
      </a-form-item>
      <a-form-item label="表单宽度">
        <a-input v-model="config.width" />
      </a-form-item>
      <a-form-item label="表单顶部外边距">
        <a-input v-model="config.marginTop" />
      </a-form-item>
      <a-form-item label="表单右边外边距">
        <a-input v-model="config.marginRight" />
      </a-form-item>
      <a-form-item label="表单底部外边距">
        <a-input v-model="config.marginBottom" />
      </a-form-item>
      <a-form-item label="表单左边外边距">
        <a-input v-model="config.marginLeft" />
      </a-form-item>
      <a-form-item label="表单属性">
        <kCheckbox
          v-if="typeof config.hideRequiredMark !== 'undefined'"
          v-model="config.hideRequiredMark"
          label="隐藏必选标记"
        />
      </a-form-item>
      <a-form-item label="提示">
        实际预览效果请点击预览查看
      </a-form-item>
    </a-form>
  </div>
</template>
<script>
// import changeOption from "@/components/ChangeOption/index.vue";
import kCheckbox from "@/components/KCheckbox/index.vue";
export default {
  name: "formProperties",
  components: {
    //   changeOption,
    kCheckbox
  },
  props: {
    config: {
      type: Object,
      required: true
    },
    previewOptions: {
      type: Object,
      required: true
    }
  },
  methods: {
    setOropertiesCentent() {
      this.$refs.propertiesCentent.style.height =
        document.body.clientHeight - 160 + "px";
    }
  },
  mounted() {
    this.setOropertiesCentent();
    window.addEventListener("resize", this.setOropertiesCentent, true);
  },
  destroyed() {
    // 取消监听
    window.removeEventListener("resize", this.setOropertiesCentent, true);
  }
};
</script>
<style lang="less" scoped>
.change-col-box {
  > div {
    padding: 5px;
    display: flex;
    > label {
      text-align: right;
      padding-right: 8px;
      display: block;
      font-size: 16px;
      width: 45px;
    }
  }
}
</style>
