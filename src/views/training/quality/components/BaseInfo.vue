<template>
  <div class="edu-adult">
    <form-generate ref="form" :fields="tab1"></form-generate>
  </div>
</template>

<script>
import FormGenerate from '@/components/FormGenerate'
import { isEmail, isPhone } from '@/utils/validate'
export default {
  name: 'BaseInfo',
  components: { FormGenerate },
  data() {
    const validatorEmail = (rule, value, callback) => {
      if (!value) {
        return callback(new Error('请输入email'))
      }
      if (!isEmail(value)) {
        return callback(new Error('email格式不正确'))
      } else {
        callback()
      }
    }
    const validatorPhone = (rule, value, callback) => {
      if (!value) {
        return callback(new Error('请输入联系电话'))
      }
      if (!isPhone(value)) {
        return callback(new Error('联系电话格式不正确'))
      } else {
        callback()
      }
    }
    return {
      tab1: [
        {
          label: '入学批次',
          field: 'pc',
          form: 'input',
          rules: [
            { required: true, message: '请输入入学批次' },
            { max: 10, message: '限制输入10位' }
          ]
        },
        {
          label: '学生姓名',
          field: 'name',
          form: 'input',
          rules: [
            { required: true, message: '请输入学生姓名' },
            { max: 10, message: '限制输入10位' }
          ]
        },
        { label: '联系电话', field: 'phone', form: 'input', rules: [{ required: true, validator: validatorPhone }] },
        {
          label: '证件种类',
          field: 'card',
          form: 'select',
          selectFrom: 'CARDTYPE_ENMU',
          rules: [{ required: true, message: '请输入证件种类' }]
        },
        {
          label: '证件号码',
          field: 'cardNo',
          form: 'input',
          rules: [
            { required: true, message: '请输入证件号码' },
            { max: 18, message: '请输入18位证件号码' }
          ]
        },
        {
          label: '民族',
          field: 'mz',
          form: 'select',
          selectFrom: 'MZ_ENMU',
          rules: [{ required: true, message: '请选择民族' }]
        },
        {
          label: '性别',
          field: 'male',
          form: 'radio',
          radioFrom: 'SEX_ENMU',
          rules: [{ required: true, message: '请选择性别' }]
        },
        { label: '出生日期', field: 'birth', form: 'date', rules: [{ required: true, message: '请选择出生日期' }] },
        {
          label: '所属省市',
          field: 'location',
          form: 'cascader',
          rules: [{ required: true, message: '请输入所属省市' }]
        },
        {
          label: '户口性质',
          field: 'xz',
          form: 'select',
          selectFrom: 'HK_ENMU',
          rules: [{ required: true, message: '请输入户口性质' }]
        },
        {
          label: '职业',
          field: 'zy',
          form: 'input',
          rules: [
            { required: true, max: 20, message: '请输入职业' },
            { max: 20, message: '限制输入20位' }
          ]
        },
        {
          label: '政治面貌',
          field: 'mm',
          form: 'select',
          selectFrom: 'ZZMM_ENMU',
          rules: [{ required: true, max: 20, message: '请选择政治面貌' }]
        },
        {
          label: '原毕业学校',
          field: 'school',
          form: 'input',
          rules: [
            { required: true, message: '请输入源毕业学校' },
            { max: 20, message: '限制输入20位' }
          ]
        },
        {
          label: '原毕业时间',
          field: 'byTime',
          form: 'date',
          rules: [{ required: true, message: '请选择原毕业时间' }]
        },
        {
          label: '原毕业证书编号',
          field: 'bookNo',
          form: 'input',
          rules: [
            { required: true, max: 20, message: '请输入原毕业证书编号' },
            { max: 15, message: '限制输入15位' }
          ]
        },
        {
          label: '原毕业证书类型',
          field: 'bookType',
          form: 'input',
          rules: [{ required: true, message: '请输入原毕业证书类型' }]
        },
        {
          label: '通讯地址',
          field: 'address',
          form: 'input',
          rules: [
            { required: true, message: '请输入通讯地址' },
            { max: 30, message: '限制输入30位' }
          ]
        },
        {
          label: '工作单位',
          field: 'work',
          form: 'input',
          rules: [
            { required: true, message: '请输入工作单位' },
            { max: 30, message: '限制输入30位' }
          ]
        },
        { label: 'email', field: 'email', form: 'input', rules: [{ required: true, validator: validatorEmail }] }
      ]
    }
  },
  mounted() {
    // this.validate()
  },
  computed: {},
  methods: {
    validate(callback) {
      const form = this.$refs.form
      form.validate(data => {
        callback && callback(data)
        console.log(data)
      })
    },
    resetForm() {
      const form = this.$refs.form
      form.reset()
    }
  }
}
</script>