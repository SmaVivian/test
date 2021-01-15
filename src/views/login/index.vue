<template>
  <div class="page-login">
    <p>登录</p>
    <v-form class="pa-5"
      ref="form"
      v-model="valid"
      lazy-validation
    >
        <!-- :counter="10" -->
      <v-text-field
        v-model="name"
        :rules="nameRules"
        label="姓名"
        required
      ></v-text-field>

      <v-text-field
        v-model="password"
        type="password"
        :rules="passwordRules"
        label="密码"
        required
      ></v-text-field>

      <v-text-field
        v-model="email"
        :rules="emailRules"
        label="邮箱"
        required
      ></v-text-field>

      <v-select
        v-model="select"
        :items="items"
        :rules="[v => !!v || 'Item is required']"
        label="Item"
        required
      ></v-select>

      <!-- <v-checkbox
        v-model="checkbox"
        :rules="[v => !!v || 'You must agree to continue!']"
        label="Do you agree?"
        required
      ></v-checkbox> -->

      <v-btn
        :disabled="!valid"
        color="success"
        class="mr-4"
        @click="validate"
      >
        校验
      </v-btn>

      <v-btn
        color="error"
        class="mr-4"
        @click="reset"
      >
        重置
      </v-btn>

      <v-btn
        color="warning"
        @click="resetValidation"
      >
        清空校验
      </v-btn>
    </v-form>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        valid: true,
        name: '',
        nameRules: [
          v => !!v || '请输入姓名',
          // v => (v && v.length <= 10) || '姓名不能超过10个字符',
        ],
        password: '',
        passwordRules: [
          v => !!v || '请输入密码',
          v => /^(?![\d]+$)(?![a-zA-Z]+$)(?![^\da-zA-Z]+$).{6,20}$/.test(v) || '6-20位必须包含数字、字母或特殊字符中的两种',
        ],
        email: '',
        emailRules: [
          v => !!v || '请输入邮箱',
          v => /.+@.+\..+/.test(v) || '邮箱格式不正确',
        ],
        select: null,
        items: [
          'Item 1',
          'Item 2',
          'Item 3',
          'Item 4',
        ],
        checkbox: false,
      }
    },
    methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
    },
  }
</script>

<style lang="scss" scoped>
.page-login {

}
</style>