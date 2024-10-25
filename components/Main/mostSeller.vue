<template>
  <div class=" flex flex-col mb-20">
    <div
      class="flex items-center justify-between mx-28 border-2 p-5 rounded-full"
    >
      <div class="flex gap-5 items-center">
        <UIcon
          size="40"
          class="text-Primary"
          name="streamline:coffee-bean-solid"
        />
        <div class="flex flex-col">
          <h1 class="font-semibold text-xl">پرفروش ترین ها</h1>
          <h2 class="font-normal">پرفروش ترین محصولات اریک کافه</h2>
        </div>
      </div>
      <UTabs
      @change="tabChange"
        :ui="{
          wrapper: 'relative space-y-0 ',
          list: { background: 'bg-gray-200', rounded: 'rounded-xl' },
        }"
        :items="items"
      />
    </div>
    <div class="flex flex-wrap gap-10 justify-center mt-4">
      <div
        v-for="i in 8"
        :key="i"
        class="flex relative flex-col items-start w-1/5 border-2 rounded-2xl my-10 p-16"
      >
        <div
          v-if="!loading"
          class="bg-black absolute top-0 text-white px-2 rounded-full left-0 mt-5 ml-5"
        >
          {{ cards[i - 1].off }}%
        </div>
        <USkeleton
          class="h-52 w-full self-center bg-contain mb-10"
          v-if="loading"
        />
        <NuxtImg
          v-else
          class="self-center w-1/2 mb-10"
          :src="cards[i - 1].img"
        />
        <USkeleton class="w-full h-5" v-if="loading" />
        <h1 v-else>{{ cards[i - 1].title }}</h1>
        <USkeleton v-if="loading" class="w-1/3 h-4 mt-3" />
        <h3 v-else class="text-gray-500 font-light">
          {{ cards[i - 1].category }}
        </h3>
        <USkeleton v-if="loading" class="w-1/2 h-8 mt-3 self-end" />
        <strike v-else class="flex self-end blur-[1px] text-stone-500">{{
          cards[i - 1].cost
        }}</strike>

        <h4 v-if="!loading" class="flex self-end gap-2 text-pink-900">
          <span>تومان</span> {{ cards[i - 1].cost }}
        </h4>
      </div>
    </div>
    <UButton class="bg-Primary text-lg rounded-full flex items-center w-fit self-center hover:bg-yellow-800 duration-150"
      ><nuxt-link to="/"> مشاهده بیشتر </nuxt-link
      ><UIcon size="25" name="material-symbols:arrow-left-alt-rounded"
    /></UButton>
  </div>
</template>
<script setup>
const loading = ref(false);

const tabChange = () => {
  loading.value = true;
  setTimeout(() => {
    loading.value = false;
  }, 1000);
};

const items = [
  {
    label: "همه دسته بندی ها",
  },
  {
    label: "آسیاب قهوه",
  },
  {
    label: "ابزار باریستا",
  },
  {
    label: "بویلر آب جوش",
  },
  {
    label: "تجهیزات کافه و رستوران",
  },
  {
    label: "شو کیک",
  },
];

const cards = [
  {
    title: "دانه قهوه باکسی برند 1",
    img: "/test.png",
    cost: "340,000",
    category: "دانه قهوه",
    off: "30",
  },
  {
    title: "دانه قهوه باکسی برند 2",
    img: "/test.png",
    cost: "340,000",
    category: "دانه قهوه",
    off: "30",
  },
  {
    title: "دانه قهوه باکسی برند 3",
    img: "/test.png",
    cost: "340,000",
    category: "دانه قهوه",
    off: "30",
  },
  {
    title: "دانه قهوه باکسی برند 4",
    img: "/test.png",
    cost: "340,000",
    category: "دانه قهوه",
    off: "30",
  },
  {
    title: "دانه قهوه باکسی برند 5",
    img: "/test.png",
    cost: "340,000",
    category: "دانه قهوه",
    off: "30",
  },
  {
    title: "دانه قهوه باکسی برند 6",
    img: "/test.png",
    cost: "340,000",
    category: "دانه قهوه",
    off: "30",
  },
  {
    title: "دانه قهوه باکسی برند 7",
    img: "/test.png",
    cost: "340,000",
    category: "دانه قهوه",
    off: "30",
  },
  {
    title: "دانه قهوه باکسی برند 8",
    img: "/test.png",
    cost: "340,000",
    category: "دانه قهوه",
    off: "30",
  },
  {
    title: "دانه قهوه باکسی برند 9",
    img: "/test.png",
    cost: "340,000",
    category: "دانه قهوه",
    off: "30",
  },
  {
    title: "دانه قهوه باکسی برند 10",
    img: "/test.png",
    cost: "340,000",
    category: "دانه قهوه",
    off: "30",
  },
];
</script>
