<template>
  <div>
    <!-- 弹窗调用设置 v-if="true" 页面调用设置 v-if="false" -->
    <template v-if="false">
      <div style="padding: 20px">
        <el-button type="primary" @click="handleFormAdd">新增表单</el-button>
      </div>
      <!-- 表单弹窗 -->
      <el-dialog
        class="genDialog"
        title=""
        :visible.sync="visibleGen"
        fullscreen
        :modal="false"
        top="0"
        :show-close="false"
      >
        <form-generator
          ref="formGenerator"
          v-if="visibleGen"
          @onClose="visibleGen = false"
          @onSave="onSaveFinish"
          :formJson="formJson"
        />
      </el-dialog>
    </template>

    <!-- 页面调用设置 -->
    <template v-else>
      <form-generator
        v-if="visibleGen2"
        ref="formGenerator"
        @onClose="visibleGen = false"
        @onSave="onSaveFinish"
        @eventForm="eventForm"
        :formJson="formJson"
      />
    </template>
  </div>
</template>

<script>
import formGenerator from '@/components/formGenerator/views/index/Home.vue'
import { setTimeout } from 'timers';
export default {
  name: 'Home',
  components: {
    formGenerator,
  },
  data() {
    return {
      // 设计表单
      visibleGen: false,
      visibleGen2: true,
      formJson: {},
      formJson_2: {
        formRef: 'elForm',
        formModel: 'formData',
        size: 'medium',
        labelPosition: 'right',
        labelWidth: 100,
        formRules: 'rules',
        gutter: 15,
        disabled: false,
        span: 24,
        formBtns: true,
        fields: [
          {
            __config__: {
              label: '用户姓名',
              labelWidth: null,
              showLabel: true,
              hideField: false,
              changeTag: true,
              tag: 'el-input',
              tagIcon: 'input',
              required: true,
              layout: 'colFormItem',
              span: 24,
              document: 'https://element.eleme.cn/#/zh-CN/component/input',
              regList: [],
              formId: 102,
              renderKey: '1021649244089285',
            },
            __slot__: {
              prepend: '',
              append: '',
            },
            placeholder: '请输入用户姓名',
            style: {
              width: '100%',
            },
            clearable: true,
            'prefix-icon': '',
            'suffix-icon': '',
            maxlength: null,
            'show-word-limit': false,
            readonly: false,
            disabled: false,
            __vModel__: 'name',
          },
          {
            __config__: {
              label: '性别',
              showLabel: true,
              labelWidth: null,
              tag: 'el-select',
              tagIcon: 'select',
              layout: 'colFormItem',
              span: 24,
              required: true,
              regList: [],
              changeTag: true,
              document: 'https://element.eleme.cn/#/zh-CN/component/select',
              formId: 103,
              renderKey: '1031649244159373',
            },
            __slot__: {
              options: [
                {
                  label: '男',
                  value: 1,
                },
                {
                  label: '女',
                  value: 2,
                },
              ],
            },
            placeholder: '请选择性别',
            style: {
              width: '100%',
            },
            clearable: true,
            disabled: false,
            filterable: false,
            multiple: false,
            __vModel__: 'sex',
          },
          {
            __config__: {
              label: '出生年月',
              tag: 'el-date-picker',
              tagIcon: 'date',
              defaultValue: null,
              showLabel: true,
              labelWidth: null,
              span: 24,
              layout: 'colFormItem',
              required: true,
              regList: [],
              changeTag: true,
              document:
                'https://element.eleme.cn/#/zh-CN/component/date-picker',
              formId: 104,
              renderKey: '1041649244179932',
            },
            placeholder: '请选择出生年月',
            type: 'date',
            style: {
              width: '100%',
            },
            disabled: false,
            clearable: true,
            format: 'yyyy-MM-dd',
            'value-format': 'yyyy-MM-dd',
            readonly: false,
            __vModel__: 'time',
          },
        ],
      },
      formJson_1: {
        fields: [
          {
            __config__: {
              layout: 'rowFormItem',
              tagIcon: 'row',
              layoutTree: true,
              document:
                'https://element.eleme.cn/#/zh-CN/component/layout#row-attributes',
              span: 24,
              formId: 101,
              renderKey: '1011646482037150',
              componentName: 'row101',
              children: [
                {
                  __config__: {
                    label: '文本',
                    showLabel: false,
                    changeTag: true,
                    labelWidth: null,
                    tag: 'j-text',
                    tagIcon: 'j-text',
                    defaultValue: '用户',
                    span: 3,
                    layout: 'colFormItem',
                    document:
                      'https://element.eleme.cn/#/zh-CN/component/button',
                    formId: 102,
                    renderKey: '1021646482038316',
                  },
                  align: 'center',
                  'line-height': 0,
                  'font-size': 14,
                  color: '#000000',
                  'font-weight': false,
                  'font-style': false,
                  'font-decoration': false,
                  __vModel__: '',
                },
                {
                  __config__: {
                    label: '用户组件',
                    showLabel: false,
                    hideField: false,
                    changeTag: true,
                    labelWidth: null,
                    tag: 'j-select-user',
                    tagIcon: 'j-select-user',
                    required: true,
                    span: 21,
                    layout: 'colFormItem',
                    regList: [],
                    document:
                      'https://element.eleme.cn/#/zh-CN/component/button',
                    formId: 103,
                    renderKey: '1031646482053043',
                  },
                  multi: false,
                  disabled: false,
                  __vModel__: 'userName',
                },
              ],
            },
            type: 'default',
            justify: 'start',
            align: 'top',
          },
          {
            __config__: {
              layout: 'rowFormItem',
              tagIcon: 'row',
              layoutTree: true,
              document:
                'https://element.eleme.cn/#/zh-CN/component/layout#row-attributes',
              span: 24,
              formId: 104,
              renderKey: '1041646482092154',
              componentName: 'row104',
              children: [
                {
                  __config__: {
                    label: '文本',
                    showLabel: false,
                    changeTag: true,
                    labelWidth: null,
                    tag: 'j-text',
                    tagIcon: 'j-text',
                    defaultValue: '部门',
                    span: 3,
                    layout: 'colFormItem',
                    document:
                      'https://element.eleme.cn/#/zh-CN/component/button',
                    formId: 105,
                    renderKey: '1051646482092154',
                  },
                  align: 'center',
                  'line-height': 0,
                  'font-size': 14,
                  color: '#000000',
                  'font-weight': false,
                  'font-style': false,
                  'font-decoration': false,
                  __vModel__: '',
                },
                {
                  __config__: {
                    label: '部门组件',
                    showLabel: false,
                    hideField: false,
                    changeTag: true,
                    labelWidth: null,
                    tag: 'j-select-dept',
                    tagIcon: 'j-select-dept',
                    required: true,
                    span: 21,
                    layout: 'colFormItem',
                    regList: [],
                    document:
                      'https://element.eleme.cn/#/zh-CN/component/button',
                    formId: 107,
                    renderKey: '1071646482106313',
                  },
                  multi: false,
                  disabled: false,
                  __vModel__: 'deptName',
                },
              ],
            },
            type: 'default',
            justify: 'start',
            align: 'top',
          },
          {
            __config__: {
              layout: 'rowFormItem',
              tagIcon: 'row',
              layoutTree: true,
              document:
                'https://element.eleme.cn/#/zh-CN/component/layout#row-attributes',
              span: 24,
              formId: 108,
              renderKey: '1081646482159345',
              componentName: 'row108',
              children: [
                {
                  __config__: {
                    label: '文本',
                    showLabel: false,
                    changeTag: true,
                    labelWidth: null,
                    tag: 'j-text',
                    tagIcon: 'j-text',
                    defaultValue: '开始时间',
                    span: 3,
                    layout: 'colFormItem',
                    document:
                      'https://element.eleme.cn/#/zh-CN/component/button',
                    formId: 109,
                    renderKey: '1091646482159345',
                  },
                  align: 'center',
                  'line-height': 0,
                  'font-size': 14,
                  color: '#000000',
                  'font-weight': false,
                  'font-style': false,
                  'font-decoration': false,
                  __vModel__: '',
                },
                {
                  __config__: {
                    label: '开始时间',
                    tag: 'el-date-picker',
                    tagIcon: 'date',
                    defaultValue: null,
                    showLabel: false,
                    labelWidth: null,
                    span: 21,
                    layout: 'colFormItem',
                    required: true,
                    regList: [],
                    changeTag: true,
                    document:
                      'https://element.eleme.cn/#/zh-CN/component/date-picker',
                    formId: 111,
                    renderKey: '1111646482186162',
                  },
                  placeholder: '请选择开始时间',
                  type: 'date',
                  style: {
                    width: '100%',
                  },
                  disabled: false,
                  clearable: true,
                  format: 'yyyy-MM-dd',
                  'value-format': 'yyyy-MM-dd',
                  readonly: false,
                  __vModel__: 'startTime',
                },
              ],
            },
            type: 'default',
            justify: 'start',
            align: 'top',
          },
          {
            __config__: {
              layout: 'rowFormItem',
              tagIcon: 'row',
              layoutTree: true,
              document:
                'https://element.eleme.cn/#/zh-CN/component/layout#row-attributes',
              span: 24,
              formId: 112,
              renderKey: '1121646482203411',
              componentName: 'row112',
              children: [
                {
                  __config__: {
                    label: '文本',
                    showLabel: false,
                    changeTag: true,
                    labelWidth: null,
                    tag: 'j-text',
                    tagIcon: 'j-text',
                    defaultValue: '结束时间',
                    span: 3,
                    layout: 'colFormItem',
                    document:
                      'https://element.eleme.cn/#/zh-CN/component/button',
                    formId: 113,
                    renderKey: '1131646482203412',
                  },
                  align: 'center',
                  'line-height': 0,
                  'font-size': 14,
                  color: '#000000',
                  'font-weight': false,
                  'font-style': false,
                  'font-decoration': false,
                  __vModel__: '',
                },
                {
                  __config__: {
                    label: '结束时间',
                    tag: 'el-date-picker',
                    tagIcon: 'date',
                    defaultValue: null,
                    showLabel: false,
                    labelWidth: null,
                    span: 21,
                    layout: 'colFormItem',
                    required: true,
                    regList: [],
                    changeTag: true,
                    document:
                      'https://element.eleme.cn/#/zh-CN/component/date-picker',
                    formId: 114,
                    renderKey: '1141646482203412',
                  },
                  placeholder: '请选择结束时间',
                  type: 'date',
                  style: {
                    width: '100%',
                  },
                  disabled: false,
                  clearable: true,
                  format: 'yyyy-MM-dd',
                  'value-format': 'yyyy-MM-dd',
                  readonly: false,
                  __vModel__: 'endTime',
                },
              ],
            },
            type: 'default',
            justify: 'start',
            align: 'top',
          },
          {
            __config__: {
              layout: 'rowFormItem',
              tagIcon: 'row',
              layoutTree: true,
              document:
                'https://element.eleme.cn/#/zh-CN/component/layout#row-attributes',
              span: 24,
              formId: 116,
              renderKey: '1161646482241703',
              componentName: 'row116',
              children: [
                {
                  __config__: {
                    label: '文本',
                    showLabel: false,
                    changeTag: true,
                    labelWidth: null,
                    tag: 'j-text',
                    tagIcon: 'j-text',
                    defaultValue: '备注：请完整填写资料。',
                    span: 24,
                    layout: 'colFormItem',
                    document:
                      'https://element.eleme.cn/#/zh-CN/component/button',
                    formId: 117,
                    renderKey: '1171646482241703',
                  },
                  align: 'left',
                  'line-height': 0,
                  'font-size': 14,
                  color: '#F20707',
                  'font-weight': true,
                  'font-style': false,
                  'font-decoration': false,
                  __vModel__: '',
                },
              ],
            },
            type: 'default',
            justify: 'start',
            align: 'top',
          },
        ],
        formRef: '请假单',
        formModel: 'formData',
        size: 'medium',
        labelPosition: 'right',
        labelWidth: 100,
        formRules: 'rules',
        gutter: 15,
        disabled: false,
        span: 24,
        formBtns: true,
      },
    }
  },
  methods: {
    handleFormAdd() {
      this.visibleGen = true

      // 有值表单测试 如需空表则注释下面代码
      this.formJson = this.formJson_1
    },
    onSaveFinish(formData) {
      console.log('formData-2:', formData)
      this.$router.push({
        name: 'Detail',
        params: {
          formData: JSON.stringify(formData),
        },
      })
    },
    // 自定义内置表单渲染
    eventForm(json){
      this.visibleGen2 = false;
      this.$nextTick(() => {
        this.formJson= json;
        this.visibleGen2= true;
      })
    },
  },
}
</script>

<style lang="scss" scoped>
.genDialog {
  ::v-deep .el-dialog__header {
    padding: 0;
  }
  ::v-deep .el-dialog__body {
    padding: 0;
  }
}
</style>
