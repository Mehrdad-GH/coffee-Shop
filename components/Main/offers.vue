<template>
  <div class="mt-20 mb-96">
    <div class="">
      <h1 class="absolute text-white right-1/2 translate-x-1/2 mt-5 text-3xl">
        تخفیفات ویژه
      </h1>
      <NuxtImg class="absolute px-28 -z-10" src="/offerBg.png" />
    </div>

    <div class="z-0 mx-40 pt-28">
      <div class="bg-white rounded-xl pt-10 shadow-md px-28">
        <div class="flex items-center border-b">
          <h1>دسته بندی ها</h1>
          <UTabs
            @change="tabChange"
            :items="tabTitle"
            :ui="{
              list: {
                background: '',

                tab: {
                  active: 'text-[#9E624C]',
                },
                marker: {
                  wrapper: ' mt-10 rounded-full ',
                  background: 'bg-[#9E624C]',
                  base: 'w-full h-1',
                },
              },
            }"
          />
        </div>
        <UButton
          @click="goPrevSlide"
          class="absolute right-[13%] mt-56 px-2 py-2 rounded-xl bg-rose-100 text-black shadow-md duration-75 hover:bg-rose-200"
        >
          <UIcon
            size="22"
            name="material-symbols-light:arrow-forward-ios-rounded"
          />
        </UButton>
        <Swiper
          ref="swiperRef"
          :modules="[SwiperAutoplay]"
          :slides-per-view="3"
          space-between="25"
          :loop="true"
          :rtl="true"
          :autoplay="{
            delay: 4000,
            disableOnInteraction: true,
          }"
          @swiper="onSwiper"
        >
          <SwiperSlide class="text-center text-black" v-for="card in cards">
            <div
              class="flex relative flex-col items-start border-2 rounded-2xl my-10 py-10 px-12"
            > 
            
            <div v-if="!loading" class="bg-black absolute top-0 text-white px-2 rounded-full left-0 mt-5 ml-5">{{ card.off }}%</div>
              <USkeleton
                class="h-52 w-full self-center bg-contain mb-10"
                v-if="loading"
              />
              <NuxtImg v-else class="self-center w-1/2 mb-10" :src="card.img" />
              <USkeleton class="w-full h-5" v-if="loading" />
              <h1 v-else>{{ card.title }}</h1>
              <USkeleton v-if="loading" class="w-1/3 h-4 mt-3" />
              <h3 v-else class="text-gray-500 font-light">
                {{ card.category }}
              </h3>
              <USkeleton v-if="loading" class="w-1/2 h-8 mt-3 self-end" />
              <strike
                v-else
                class="flex self-end blur-[1px] text-stone-500"
                >{{ card.cost }}</strike
              >
              
              <h4 v-if="!loading"class="flex self-end gap-2 text-pink-900">
                <span>تومان</span> {{ card.cost }}
              </h4>
            </div>
          </SwiperSlide>
        </Swiper>
        <UButton
          class="absolute left-[13%] -mt-64 -translate-y-5 px-2 py-2 rounded-xl bg-rose-100 text-black shadow-md duration-75 hover:bg-rose-200"
          @click="goNextSlide"
        >
          <UIcon size="22" name="material-symbols-light:arrow-back-ios-new" />
        </UButton>
      </div>
    </div>
  </div>
</template>
<script setup>
const swiperRef = ref(null);
const loading = ref(false);

// Save swiper instance reference
const onSwiper = (swiperInstance) => {
  swiperRef.value = swiperInstance;
};

const tabChange = () => {
  loading.value = true;
  setTimeout(() => {
    loading.value = false;
  }, 1000);
};

// Go to previous slide
const goPrevSlide = () => {
  if (swiperRef.value) {
    swiperRef.value.slidePrev();
  }
};

// Go to next slide
const goNextSlide = () => {
  if (swiperRef.value) {
    swiperRef.value.slideNext();
  }
};

const tabTitle = [
  {
    label: "دانه قهوه",
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
    img: "/test2.png",
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
    img: "/test2.png",
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
    img: "/test2.png",
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
];
</script>
