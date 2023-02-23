<template>
  <router-link v-if="blog" :to="{ name: 'blogPost', params: { blogId: blog._id } }">

    <div class="card m-3">

      <div class="row">

        <div class="col-8">
          <router-link :to="{ name: 'Profile', params: { profileId: blog.creatorId } }">

            <span class="m-1 p-2">
              <img class="avatar rounded-circle" :src="blog.creator.picture" alt="">
              <span class="p-2">{{ blog.creator.name }}</span>

            </span>
          </router-link>
          <b>
            <p class="p-3">{{ blog.title }}</p>
          </b>
          <p class="p-3 abr" maxLength="10">{{ blog.body }}</p>

        </div>
        <div class="col-4 ">
          <div class="p-2">
            <img class="rounded border-dark border img-fluid blogImg" :src="blog.imgUrl" alt="">

          </div>
        </div>
      </div>
    </div>
  </router-link>
</template>


<script>
import { Blog } from "../models/Blog.js";

export default {
  props: {
    blog: {
      type: Blog,
      required: true
    }
  },
  setup() {

    return {

    }
  }
}
</script>


<style lang="scss" scoped>
.avatar {
  height: 2em;
  width: 2em;

}

.abr {
  overflow: hidden;
  max-height: 10vh;
}

.blogImg {
  max-height: 20vh;
  width: 100%;
  object-fit: cover;
}

.card {
  max-height: 30vh;
  color: black;
}
</style>