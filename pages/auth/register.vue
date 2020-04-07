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
            <input
              type="text"
              name="name"
              v-model.trim="form.name"
              class="form-control form-control-lg font-14 fw-300"
              :class="{ 'is-invalid': form.errors.has('name') }"
              placeholder="名前"
            />
            <has-error :form="form" field="name"></has-error>
          </div>
          <div class="form-group">
            <input
              type="text"
              name="username"
              v-model.trim="form.username"
              class="form-control form-control-lg font-14 fw-300"
              :class="{ 'is-invalid': form.errors.has('username') }"
              placeholder="アカウント名"
            />
            <has-error :form="form" field="username"></has-error>
          </div>
          <div class="form-group">
            <input
              type="text"
              name="email"
              v-model.trim="form.email"
              class="form-control form-control-lg font-14 fw-300"
              :class="{ 'is-invalid': form.errors.has('email') }"
              placeholder="メールアドレス"
            />
            <has-error :form="form" field="email"></has-error>
          </div>
          <div class="form-group">
            <input
              type="password"
              name="password"
              v-model.trim="form.password"
              class="form-control form-control-lg font-14 fw-300"
              :class="{ 'is-invalid': form.errors.has('password') }"
              placeholder="パスワード"
            />
            <has-error :form="form" field="password"></has-error>
          </div>
          <div class="form-group">
            <input
              type="password"
              name="password_confirmation"
              v-model.trim="form.password_confirmation"
              class="form-control form-control-lg font-14 fw-300"
              :class="{ 'is-invalid': form.errors.has('password_confirmation') }"
              placeholder="パスワード確認"
            />
            <has-error :form="form" field="password_confirmation"></has-error>
          </div>
          <div class="text-right">
            <button
              type="submit"
              :disabled="form.busy"
              class="btn btn-primary primary-bg-color font-16 fw-500 text-uppercase"
            >
              <span v-if="form.busy">
                <i class="fas fa-spinner fa-spin"></i>
              </span>
              登録
            </button>
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
      }
    }
  }
</script>

<style scoped>

</style>
