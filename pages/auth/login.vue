<template>
  <div class="wrapper">

    <!-- Section Cards -->
    <section class="authentication">
      <div class="auth-body">
        <h1 class="text-uppercase fw-500 mb-4 text-center font-22">
          ログイン
        </h1>
        <form class="auth-form" action="" method="">
          <div class="form-group">
            <input
              type="text"
              name="email"
              class="form-control form-control-lg font-14 fw-300"
              placeholder="メールアドレス"
            />
          </div>
          <div class="form-group">
            <input
              type="password"
              name="password"
              class="form-control form-control-lg font-14 fw-300"
              placeholder="パスワード"
            />
          </div>
          <div class="mt-4 mb-4 clearfix">
            <a class="forgot-pass color-blue font-14 fw-400" href="#">パスワードを忘れた方はこちら</a>
          </div>
          <div class="text-right">
            <button type="submit" class="btn btn-primary primary-bg-color font-16 fw-500 text-uppercase">
              ログイン
            </button>
          </div>
          <p class="font-14 fw-400 text-center mt-4">
            アカウントを持っていない方は
            <a class="color-blue" href="#">こちら</a>
          </p>
        </form>
      </div>
    </section>
    <!-- End Cards -->
  </div>
</template>

<script>
    export default {
        name: "login"
    }
</script>

<style scoped>

</style>
