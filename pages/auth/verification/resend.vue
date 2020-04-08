<template>
  <div class="wrapper">

    <!-- Section Cards -->
    <section class="authentication">
      <div class="auth-body">
        <h1 class="text-uppercase fw-500 mb-4 text-center font-22">
          確認メールの再送信
        </h1>
        <form class="auth-form" @submit.prevent="submit">
          <alert-error v-if="form.errors.has('message')" :form="form">
            {{ form.errors.get('message') }}
          </alert-error>
          <alert-success :form="form">
            確認メールを送信しました
          </alert-success>
          <div class="form-group">
            <base-input
              :form="form"
              field="email"
              v-model="form.email"
              placeholder="メールアドレス"
            />
          </div>

          <div class="text-right">
            <base-button :loading="form.busy">
              送信
            </base-button>
          </div>
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
              email: ''
            })
          }
        },
      methods: {
          submit() {
            this.form.post(`/verification/resend`)
              .then(res => this.form.reset())
              .catch(error => console.log(error));
          }
      }
    }
</script>

<style scoped>

</style>
