<template>
  <div class="wrapper">

    <!-- Section Cards -->
    <section class="authentication">
      <div class="auth-body">
        <h1 class="text-uppercase fw-500 mb-4 text-center font-22">
          新規登録
        </h1>
        <form class="auth-form" @submit.prevent="submit">
          <alert-success :form="form">
            確認メールを送信しました
          </alert-success>
          <div class="form-group">
            <base-input
              :form="form"
              field="name"
              v-model.trim="form.name"
              placeholder="名前"
            />
          </div>
          <div class="form-group">
            <base-input
              :form="form"
              inputType="text"
              field="username"
              v-model.trim="form.username"
              placeholder="アカウント名"
            />
          </div>
          <div class="form-group">
            <base-input
              :form="form"
              inputType="email"
              field="email"
              v-model.trim="form.email"
              placeholder="メールアドレス"
            />
          </div>
          <div class="form-group">
            <base-input
              :form="form"
              inputType="password"
              field="password"
              v-model.trim="form.password"
              placeholder="パスワード"
            />
          </div>
          <div class="form-group">
            <base-input
              :form="form"
              inputType="password"
              field="password_confirmation"
              name="password_confirmation"
              v-model.trim="form.password_confirmation"
              placeholder="パスワード確認"
            />
          </div>
          <div class="text-right">
            <base-button :loading="form.busy">
              登録
            </base-button>
          </div>
          <p class="font-14 fw-400 text-center mt-4">
            アカウントを持っている方はこちら
            <nuxt-link :to="{ name: 'login' }" class="color-blue"> ログイン</nuxt-link>
          </p>
        </form>
      </div>
    </section>
    <!-- End Cards -->
  </div>
</template>

<script>
  export default {
    middleware: ['guest'],
    data() {
      return {
        form: this.$vform({
          username: '',
          name: '',
          email: '',
          password: '',
          password_confirmation: ''
        })
      }
    },
    methods: {
      submit() {
        this.form.post(`/register`)
          .then(res => {
            this.form.reset();
            console.log(res)
          }).catch(error => {
          console.log(error)
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>

<style></style>
