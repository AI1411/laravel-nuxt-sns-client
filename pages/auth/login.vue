<template>
  <div class="wrapper">

    <!-- Section Cards -->
    <section class="authentication">
      <div class="auth-body">
        <h1 class="text-uppercase fw-500 mb-4 text-center font-22">
          ログイン
        </h1>
        <form class="auth-form" @submit.prevent="submit">
          <alert-error v-if="form.errors.has('message')" :form="form">
            {{ form.errors.get('message') }}
            <nuxt-link :to="{ name: 'verification.resend' }"
            >Resend verification email
            </nuxt-link
            >
          </alert-error>
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
          <div class="form-group">
            <input
              type="password"
              name="password"
              v-model="form.password"
              class="form-control form-control-lg font-14 fw-300"
              :class="{'is-invalid' : form.errors.has('password')}"
              placeholder="パスワード"
            />
            <has-error :form="form" field="password"></has-error>
          </div>
          <div class="mt-4 mb-4 clearfix">
            <nuxt-link :to="{name: 'password.email'}" class="forgot-pass color-blue font-14 fw-400">パスワードを忘れた方はこちら
            </nuxt-link>
          </div>
          <div class="text-right">
            <base-button :loading="form.busy">
              ログイン
            </base-button>
          </div>
          <p class="font-14 fw-400 text-center mt-4">
            アカウントを持っていない方は
            <nuxt-link :to="{ name: 'register' }" class="color-blue">こちら</nuxt-link>
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
          email: '',
          password: ''
        })
      }
    },
    methods: {
      submit() {
        this.$auth
          .loginWith('local', {
            data: this.form
          })
          .then(res => {
            console.log(res);
          })
          .catch(e => {
            this.form.errors.set(e.response.data.errors);
          });
      }
    }
  }
</script>

<style scoped>

</style>
