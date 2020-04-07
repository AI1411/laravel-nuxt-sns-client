<template>
  <div class="wrapper">

    <!-- Section Cards -->
    <section class="authentication">
      <div class="auth-body">
        <h1 class="text-uppercase fw-500 mb-4 text-center font-22">
          新規登録
        </h1>
        <form class="auth-form">
          <div class="form-group">
            <input
              type="text"
              name="name"
              class="form-control form-control-lg font-14 fw-300"
              placeholder="名前"
            />
          </div>
          <div class="form-group">
            <input
              type="text"
              name="username"
              class="form-control form-control-lg font-14 fw-300"
              placeholder="アカウント名"
            />
          </div>
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
          <div class="form-group">
            <input
              type="password"
              name="password_confirmation"
              class="form-control form-control-lg font-14 fw-300"
              placeholder="パスワード確認"
            />
          </div>

          <div class="text-right">
            <button type="submit" class="btn btn-primary primary-bg-color font-16 fw-500 text-uppercase">
              登録
            </button>
          </div>
          <p class="font-14 fw-400 text-center mt-4">
            アカウントを持っている方はこちら
            <a class="color-blue" href="#"> ログイン</a>
          </p>
        </form>
      </div>
    </section>
    <!-- End Cards -->
  </div>
</template>

<script>
    export default {
        name: "register"
    }
</script>

<style scoped>

</style>
