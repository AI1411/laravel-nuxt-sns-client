<template>
  <section class="authentication">
    <div class="auth-body">
      <h1 class="text-uppercase fw-500 mb-4 text-center font-22">
        パスワードリセット
      </h1>
      <form class="auth-form" @submit.prevent="submit">
        <alert-success :form="form">{{ status }}</alert-success>
        <div class="form-group">
          <input
            type="text"
            name="email"
            v-model="form.email"
            class="form-control form-control-lg font-14 fw-300"
            :class="{'is-invalid': form.errors.has('email')}"
            placeholder="メールアドレス"
          />
          <has-error :form="form" field="email"></has-error>
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
            ログイン
          </button>
        </div>
        <p class="font-14 fw-400 text-center mt-4">
          アカウントを持っていない方は
          <nuxt-link :to="{ name: 'login' }" class="color-blue">こちら</nuxt-link>
        </p>
      </form>
    </div>
  </section>
</template>

<script>
  export default {
    data() {
      return {
        form: this.$vform({
          email: '',
        }),
        status: ''
      }
    },
    methods: {
      submit() {
        this.form.post('/password/email')
        .then(res => {
          this.status = res.data.status
          this.form.reset();
          // console.log(res)
        }).catch(e => {
          console.log(e);
        })
      }
    }
  }
</script>

<style scoped>

</style>
