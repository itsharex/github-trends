<script setup lang='ts'>
import dayjs from '~/utils/day'

defineProps(['user', 'index'])
</script>

<template>
  <div v-slidein="100" relative overflow-hidden rounded-md p2 flex="~ items-center" border="~ dark:gray-600/80 hover:primary">
    <OrderNum :index="index" />
    <LazyImage :src="user.avatar_url" mr2 />
    <div min-w-0 space-y-1>
      <a :href="user.html_url" target="_blank" text-lg>
        <span mr-2 font-semibold text="blue-500 hover:purple-500">{{ user.name }}</span>
        <span font-light text="slate-400 dark:slate-500/90"> {{ user.login }}</span>
      </a>
      <div flex gap-3>
        <IconText icon-name="ph:users-four" title="粉丝数量" :text="user.followers" text-pink-500 />
        <IconText icon-name="teenyicons:git-outline" title="仓库数量" :text="user.public_repos" text-violet-500 />
        <IconText icon-name="ic:outline-update" title="最近更新" :text="dayjs(user.updated_at).fromNow() " text-green-500 />
      </div>
      <div gap-3 text="slate-500 lt-md:xs" flex="~ wrap">
        <IconText icon-name="ph:buildings-bold" title="公司" :text="user.company" />
        <IconText icon-name="ph:map-pin-line-bold" title="位置" :text="user.location" />
        <IconText icon-name="material-symbols:attach-email-outline" title="邮箱" :text="user.email" />
      </div>
      <p text="blue-600 hover:purple-500">
        <a :href="user.blog" target="_blank">{{ user.blog }}</a>
      </p>
    </div>
  </div>
</template>

<style scoped lang='scss'>

</style>
