<script setup lang="ts">
useSeoMeta({ title: 'Blogs' })
</script>

<template>
  <div>
    <h1 class="pb-4">
      Blogs
    </h1>
    <content-list v-slot="{ list }" path="/blogs">
      <div class="divide-y divide-gray divide-op-20 divide-dashed dark:(divide-zinc divide-op-25)">
        <template
          v-for="blog in list.sort((a, b) => +new Date(b.date) - +new Date(a.date))"
          :key="blog._path"
        >
          <div class="flex flex-col items-start py-2 md:flex-row">
            <h3 class="my-2 flex-auto md:m-a">
              <nuxt-link :to="blog._path">
                {{ blog.title }}
              </nuxt-link>
            </h3>
            <p class="my-0 op-70 md:(my-a ml-12 min-w-fit)">
              {{ useDateFormat(blog.date, 'DD MMMM YYYY') }}
            </p>
          </div>
        </template>
      </div>
    </content-list>
  </div>
</template>
