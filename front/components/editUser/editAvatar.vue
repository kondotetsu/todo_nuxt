<template>
  <v-form
    ref="form"
    lazy-validation
    class="mb-6"
  >
    <v-row class="pt-4 pl-3">
      <v-icon>mdi-account-box</v-icon>
      <span>ユーザー画像</span>
    </v-row>
    <v-row
      justify="center"
      class="pt-6"
    >
      <v-avatar size="150">
        <template v-if="imageFile !== null">
          <v-img
            v-if="url == null"
            :src="defaultImg"
          />
          <v-img
            v-else
            :src="url"
          />
        </template>
        <template v-else>
          <v-img :src="defaultImg" />
        </template>
      </v-avatar>
      <v-col cols="12">
        <input
          id="image-files"
          ref="image_files"
          accept="image/png, image/jpeg, image/bmp"
          prepend-icon="mdi-image"
          label="画像を選択してください"
          class="pt-14"
          type="file"
          @change="setImage"
        >
      </v-col>
    </v-row>
  </v-form>
</template>

<script>
export default {
  data() {
    return {
      imageFile: [],
      url: '',
      defaultImg: require('@/assets/images/default_user_icon.jpeg'),
    };
  },
  mounted() {
    this.fetchUser();
  },
  methods: {
    setImage(e) {
      e.preventDefault();
      this.imageFile = e.target.files[0];
      this.upload();
    },
    async upload() {
      let formData = new FormData();
      if (this.imageFile !== null) {
        formData.append('image', this.imageFile);
      }
      this.createPost(formData);
    },
    async fetchUser(get) {
      const url = 'https://todonuxt-api.herokuapp.com/api/v1/current_user';
      const response = await this.$axios.get(url, get);
      this.url = response.data.url;
    },
    async createPost(post) {
      const url = 'https://todonuxt-api.herokuapp.com/api/v1/users';
      const response = await this.$axios.post(url, post);
      this.url = response.data.url;
      this.$store.dispatch('image/doSearch');
    },
  },
};
</script>
