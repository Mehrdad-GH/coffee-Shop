<template>
  <div class="mt-5 mx-16">
    <div class="flex justify-between items-center">
      <div class="text-left text-lg flex items-center">
        <h1>
          <span class="text-Primary"> -021</span><br />
          123456789
        </h1>

        <div class="bg-red-100 flex rounded-full shadow-2xl p-3 mr-4">
          <UIcon class="text-Primary" name="ph:coffee-bean-fill" size="30" />
        </div>
      </div>

      <NuxtLink to="/"><NuxtImg class="h-10" src="/logo.png" /></NuxtLink>

      <div class="flex">
        <div
          class="rounded-full px-6 py-2 my-2 border-2 border-black hover:bg-black hover:text-white duration-300"
        >
          ورود / ثبت نام
        </div>
        <UButton
          class="rounded-full bg-Primary px-3 m-2 border-2 hover:bg-white hover:text-black hover:border-black duration-500"
          icon="ic:outline-shopping-bag"
          :padded="false"
        ></UButton>
      </div>
    </div>

    <div
      class="flex justify-between items-center bg-[#28221E] text-white w-full rounded-full pr-10 mt-5 py-3 relative"
    >
      <ul class="flex gap-10">
        <li>صفحه اصلی</li>
        <li class="relative group flex">
          لیست محصولات
          <UIcon
            class="mt-1"
            name="material-symbols:keyboard-arrow-down-rounded"
          />
          <ul
            @mouseenter="flag.value = true"
            @mouseleave="flag.value = flase"
            :class="flag.value ? 'false' : 'hidden'"
            class="absolute group-hover:block bg-[#38322E] mt-5 text-white rounded-lg p-3"
          >
            <li class="py-1 px-5 hover:bg-[#28221E] rounded">محصول ۱</li>
            <li class="py-1 px-5 hover:bg-[#28221E] rounded">محصول ۲</li>
            <li class="py-1 px-5 hover:bg-[#28221E] rounded">محصول ۳</li>
          </ul>
        </li>
        <li>خدمات</li>
        <li>آموزش ها</li>
        <li>درباره ما</li>
        <li>تماس با ما</li>
      </ul>

      <div class="flex bg-[#FFFFFF33] p-2 rounded-full ml-5 gap-2 px-3">
        <h1>Eric.Cafe</h1>
        <UIcon class="-mt-0.5" size="25" name="ph:instagram-logo-bold" />
      </div>
    </div>
  </div>
</template>

<script setup>
const flag = ref(false);
</script>
