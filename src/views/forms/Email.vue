<template>
  <div>
    <!-- Hero -->
    <base-page-heading title="Email Template" subtitle="Automate your email reporting">
      <template #extra>
        <b-breadcrumb class="breadcrumb-alt">
          <b-breadcrumb-item href="javascript:void(0)">Forms</b-breadcrumb-item>
          <b-breadcrumb-item active>Template</b-breadcrumb-item>
        </b-breadcrumb>
      </template>
    </base-page-heading>
    <!-- END Hero -->

    <!-- Page Content -->
    <div class="content">
      <!-- Vue SimpleMDE -->
      <base-block rounded title="Shortlisted Candidates" header-bg>
              <template #options>
                <b-button type="submit" size="sm" variant="primary">
                  Submit
                </b-button>
                <b-button type="reset" size="sm" variant="alt-primary">
                  Reset
                </b-button>
              </template>
        <vue-simplemde v-model="simplemdeData" ref="markdownEditor" :configs="simplemdeConfig"></vue-simplemde>
      </base-block>
      <!-- END Vue SimpleMDE -->
      <!-- Vue SimpleMDE -->
      <base-block rounded title="Regected Candidates" header-bg>
              <template #options>
                <b-button type="submit" size="sm" variant="danger">
                  Submit
                </b-button>
                <b-button type="reset" size="sm" variant="alt-danger">
                  Reset
                </b-button>
              </template>
        <vue-simplemde v-model="simplemdeData" ref="markdownEditor" :configs="simplemdeConfig"></vue-simplemde>
      </base-block>
      <!-- END Vue SimpleMDE -->
      <!-- Vue SimpleMDE -->
      <base-block rounded title="Waiting Candidates" header-bg>
              <template #options>
                <b-button type="submit" size="sm" variant="warning">
                  Submit
                </b-button>
                <b-button type="reset" size="sm" variant="alt-warning">
                  Reset
                </b-button>
              </template>
        <vue-simplemde v-model="simplemdeData" ref="markdownEditor" :configs="simplemdeConfig"></vue-simplemde>
      </base-block>
      <!-- END Vue SimpleMDE -->
    </div>
    <!-- END Page Content -->
  </div>
</template>

<style lang="scss">

// SimpleMDE + Custom overrides
@import '~simplemde/dist/simplemde.min.css';
@import './src/assets/scss/vendor/simplemde';
</style>

<script>
// Vue SimpleMDE, for more info and examples you can check out https://github.com/F-loat/vue-simplemde
import VueSimplemde from 'vue-simplemde'

//import InlineEditor from '@ckeditor/ckeditor5-build-inline'
//import BalloonEditor from '@ckeditor/ckeditor5-build-balloon'
//import BalloonBlockEditor from '@ckeditor/ckeditor5-build-balloon-block'

export default {
  components: {
    VueSimplemde
  },
  data () {
    return {      
      simplemdeData: 'Hello SimpleMDE!',
      simplemdeConfig: {
        autoDownloadFontAwesome: false,
      }
    }
  },
  mounted () {
    // Change SimpleMDE's Font Awesome 4 Icons with Font Awesome 5
    let simplemdeLinkHeading = document.querySelector('.editor-toolbar > a.fa-header')
    let simplemdeLinkPicture = document.querySelector('.editor-toolbar > a.fa-picture-o')

    simplemdeLinkHeading.classList.remove('fa-header')
    simplemdeLinkHeading.classList.add('fa-heading')
    
    simplemdeLinkPicture.classList.remove('fa-picture-o')
    simplemdeLinkPicture.classList.add('fa-image')
  }
}
</script>
