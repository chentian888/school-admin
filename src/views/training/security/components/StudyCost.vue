<template>
  <div class="edu-adult">
    <form-generate ref="form" :fields="tab6"></form-generate>
  </div>
</template>

<script>
import FormGenerate from '@/components/FormGenerate'
import { isMoney } from '@/utils/validate'
export default {
  name: 'StudyCost',
  components: { FormGenerate },
  data() {
    const validatorMoney = text => {
      return (rule, value, callback) => {
        if (!value) {
          return callback()
        }
        if (!isMoney(value)) {
          return callback(new Error(`${text}格式不正确`))
        } else {
          callback()
        }
      }
    }
    return {
      tab6: [
        {
          label: '批次',
          field: 'name',
          form: 'select',
          rules: [{ max: 15, message: '批次限制输入15位' }]
        },
        {
          label: '层次',
          field: 'phone',
          form: 'select',
          rules: [{ max: 15, message: '层次限制输入15位' }]
        },
        {
          label: '院校',
          field: 'card',
          form: 'input',
          rules: [{ max: 20, message: '院校限制输入20位' }]
        },
        {
          label: '姓名',
          field: 'cardNo',
          form: 'input',
          rules: [{ max: 15, message: '姓名限制输入15位' }]
        },
        {
          label: '专业',
          field: 'mz',
          form: 'input',
          rules: [{ max: 15, message: '限制输入15位' }]
        },
        {
          label: '身份证号',
          field: 'meal',
          form: 'input',
          rules: [{ max: 18, message: '身份证号限制输入18位' }]
        },
        {
          label: '录入时间',
          field: 'birth',
          form: 'date',
          rules: []
        },
        {
          label: '总学费',
          field: 'location',
          form: 'input',
          rules: [{ validator: validatorMoney('总学费') }]
        },
        {
          label: '实际学费',
          field: 'xz',
          form: 'input',
          rules: [{ validator: validatorMoney('实际学费') }]
        },
        {
          label: '欠款',
          field: 'zy',
          form: 'input',
          rules: [{ validator: validatorMoney('欠款') }]
        },
        {
          label: '第一年交费',
          field: 'mm',
          form: 'input',
          rules: [{ validator: validatorMoney('第一年交费') }]
        },
        {
          label: '第二年交费',
          field: 'school',
          form: 'input',
          rules: [{ validator: validatorMoney('第二年交费') }]
        },
        {
          label: '第三年交费',
          field: 'byTime',
          form: 'input',
          rules: [{ validator: validatorMoney('第三年交费') }]
        },
        {
          label: '第四年交费',
          field: 'bookNo',
          form: 'input',
          rules: [{ validator: validatorMoney('第四年交费') }]
        },
        {
          label: '第五年交费',
          field: 'bookType',
          form: 'input',
          rules: [{ validator: validatorMoney('第五年交费') }]
        },
        {
          label: '报考费',
          field: 'address',
          form: 'input',
          rules: [{ validator: validatorMoney('报考费') }]
        },
        {
          label: '入学考试辅导费',
          field: 'work',
          form: 'input',
          rules: [{ validator: validatorMoney('入学考试辅导费') }]
        },
        {
          label: '学位报考费',
          field: 'email',
          form: 'input',
          rules: [{ validator: validatorMoney('学位报考费') }]
        },
        {
          label: '学位辅导费',
          field: 'aa',
          form: 'input',
          rules: [{ validator: validatorMoney('学位辅导费') }]
        },
        {
          label: '网课费',
          field: 'bb',
          form: 'input',
          rules: [{ validator: validatorMoney('网课费') }]
        },
        {
          label: '论文费',
          field: 'cc',
          form: 'input',
          rules: [{ validator: validatorMoney('论文费') }]
        },
        {
          label: '图像采集费',
          field: 'dd',
          form: 'input',
          rules: [{ validator: validatorMoney('图像采集费') }]
        }
      ]
    }
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
<style lang="less"></style>