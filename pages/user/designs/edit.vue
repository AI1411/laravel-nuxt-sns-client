<template>
  <div class="wrapper">
    <!-- Start Hero -->
    <section class="hero text-center bg-secondary mb-4 text-white">
      <div class="container">
        <h1 class="font-28 fw-600 text-uppercase">
          Upload a design
        </h1>
      </div>
    </section>
    <!-- End Hero -->

    <!-- Upload Shot -->
    <div class="upload-shot">
      <div class="container">
        <div class="row">
          <div class="col-md-5">
            <div class="upload white-bg-color text-center">
              <div class="box-input">
                <div class="uload-icon font-28">
                  <i class="fas fa-cloud-upload-alt"></i>
                </div>
                <label class="fileContainer font-18 fw-500">
                  <input type="file"/>
                  <span
                  >Drag an image here or
                                            <a>Browse</a> for an image to
                                            upload.</span
                  >
                </label>
              </div>
            </div>
          </div>
          <div class="col-md-7">
            <h4>Update Design Information</h4>
          </div>

        </div>
      </div>
    </div>
    <!-- End Upload Shot -->
  </div>
</template>

<script>
  export default {
    data() {
      return {
        form: this.$vform({
          title: '',
          description: '',
          is_live: false,
          tags: [],
          assign_to_team: false,
          team: null
        })
      }
    },
    async asyncData({$axios, params, error, redirect}) {
      try {
        const design = await $axios.$get(`/designs/${params.id}`);
        return {design: design.data};
      } catch (err) {
        if (err.response.status === 404) {
          error({statusCode: 404, message: '投稿がありません'})
        } else {
          error({statusCode: 500, message: 'サーバーエラー'})
        }
      }
    },
    methods: {
      submit() {

      }
    },
    mounted() {
      if (this.design) {
        Object.keys(this.form).forEach(key => {
          if (this.design.hasOwnProperty(key)) {
            this.form[key] = this.design[key]
          }
        })
        this.form.tags = this.design.tag_list.tags || []

        if (this.design.team) {
          this.form.team = this.design.team.id;
          this.form.assign_to_team = true;
        } else {
          this.form.assign_to_team = false;
        }
      }
    }
  }
</script>

<style scoped>

</style>
