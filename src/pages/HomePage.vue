<template>
  <div class="container-fluid">
    <div class="row">
      <div v-for="blog in blogs" class="col-md-8 m-auto">
        <BlogCard :blog="blog" />

      </div>
    </div>
  </div>
</template>

<script>
import { onMounted, computed } from "vue";
import { logger } from "../utils/Logger.js";
import Pop from "../utils/Pop.js";
import { blogsService } from "../services/BlogsService.js";
import { AppState } from "../AppState.js";

export default {
  setup() {
    async function getBlogs() {
      try {
        await blogsService.getBlogs()
      } catch (error) {
        Pop.error(error.message)
        logger.error(error)

      }
    }
    onMounted(() => {
      getBlogs();
    })
    return {
      blogs: computed(() => AppState.blogs)
    }
  }
}
</script>

<style scoped lang="scss"></style>
