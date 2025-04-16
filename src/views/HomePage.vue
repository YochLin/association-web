<template>
  <div>
    <!-- 輪播圖部分 -->
    <section class="relative">
      <div class="carousel-container relative overflow-hidden h-[500px] md:h-[600px]">
        <div 
          v-for="(slide, index) in slides" 
          :key="index" 
          :class="['carousel-slide absolute inset-0 transition-opacity duration-1000', 
                  currentSlide === index ? 'opacity-100' : 'opacity-0']"
        >
          <img :src="slide.image" :alt="slide.title" class="w-full h-full object-cover">
          <div class="absolute inset-0 bg-black bg-opacity-40 flex items-center justify-center p-4">
            <div class="text-center text-white max-w-4xl">
              <h2 class="text-3xl md:text-5xl font-bold mb-4">{{ slide.title }}</h2>
              <p class="text-xl md:text-2xl mb-6">{{ slide.description }}</p>
              <router-link :to="slide.link" class="btn btn-primary px-6 py-3">
                了解更多
              </router-link>
            </div>
          </div>
        </div>
        
        <!-- 輪播圖控制按鈕 -->
        <div class="absolute bottom-4 left-0 right-0 flex justify-center space-x-2">
          <button 
            v-for="(_, index) in slides" 
            :key="index"
            @click="currentSlide = index"
            :class="['w-3 h-3 rounded-full', currentSlide === index ? 'bg-white' : 'bg-gray-400']"
          ></button>
        </div>
      </div>
    </section>
    
    <!-- 協會簡介部分 -->
    <section class="py-16 bg-white">
      <div class="container-custom">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold text-gray-800 mb-4">關於我們的協會</h2>
          <div class="w-20 h-1 bg-blue-600 mx-auto"></div>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
          <div>
            <img src="/about-placeholder.jpg" alt="協會介紹" class="rounded-lg shadow-lg w-full h-auto">
          </div>
          <div>
            <h3 class="text-2xl font-semibold text-gray-800 mb-4">我們的使命</h3>
            <p class="text-gray-600 mb-6 leading-relaxed">
              本會前身「台灣早餐速食促進協會」，由多家早餐速食業之翹楚所共同努力促成之，奉內政部台內社字第0930071455號許可並於94年2月25日正式成立並推選張廷章先生擔任創會理事長，
              本著以同業聯盟及經驗分享為宗旨，共同致力於促進速食連鎖加盟事業之健全發展。
            </p>
            <p class="text-gray-600 mb-6 leading-relaxed">
              經第二屆理事長蔡澔鎔先生努力，第三屆會員大會提案正式通過並奉內政部台內社字第0980037539號許
              可核准正名為「台灣速食餐飲協會」，更名首屆理事長為葉益芳先生。 
              未來，本會將秉持專業的態度，提供會員教育講習、海外市場經營資訊、供應鏈輔導諮詢等業務，期望本會成為兩岸速食餐飲產業最大服務平台的願景得以實現。
            </p>
            <router-link to="/about" class="btn btn-primary">詳細了解</router-link>
          </div>
        </div>
      </div>
    </section>
    
    <!-- 最新活動部分 -->
    <section class="py-16 bg-gray-100">
      <div class="container-custom">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold text-gray-800 mb-4">最新活動</h2>
          <div class="w-20 h-1 bg-blue-600 mx-auto"></div>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="(event, index) in events" :key="index" class="card">
            <img :src="event.image" :alt="event.title" class="w-full h-48 object-cover">
            <div class="p-6">
              <div class="flex items-center text-gray-500 mb-2">
                <svg class="h-5 w-5 mr-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
                </svg>
                {{ event.date }}
              </div>
              <h3 class="text-xl font-semibold text-gray-800 mb-2">{{ event.title }}</h3>
              <p class="text-gray-600 mb-4">{{ event.description }}</p>
              <router-link :to="`/events/${event.id}`" class="text-blue-600 font-medium hover:text-blue-800">
                查看詳情 &rarr;
              </router-link>
            </div>
          </div>
        </div>
        
        <div class="text-center mt-10">
          <router-link to="/events" class="btn btn-primary">查看所有活動</router-link>
        </div>
      </div>
    </section>
    
    <!-- 合作品牌部分 -->
    <section class="py-16 bg-white">
      <div class="container-custom">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold text-gray-800 mb-4">合作品牌</h2>
          <div class="w-20 h-1 bg-blue-600 mx-auto"></div>
          <p class="text-gray-600 mt-4 max-w-2xl mx-auto">我們與行業領先的品牌和組織建立了戰略合作伙伴關係，共同推動行業發展</p>
        </div>
        
        <div class="grid grid-cols-2 md:grid-cols-4 gap-6 items-center">
          <div v-for="i in 8" :key="i" class="flex justify-center">
            <div class="p-4 bg-gray-50 rounded-lg w-full h-32 flex items-center justify-center">
              <img :src="`/brand-placeholder-${i}.png`" :alt="`品牌合作伙伴 ${i}`" class="max-h-16 max-w-full">
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

// 輪播圖數據
const slides = [
  {
    title: "歡迎訪問協會官網",
    description: "我們致力於促進行業交流與合作，推動行業健康發展",
    image: "/slide-1.jpg",
    link: "/about"
  },
  {
    title: "專業的行業支持",
    description: "為會員提供全方位的專業諮詢和支持服務",
    image: "/slide-2.jpg",
    link: "/services"
  },
  {
    title: "定期舉辦行業活動",
    description: "研討會、培訓課程、社交活動等多種形式的專業交流",
    image: "/slide-3.jpg",
    link: "/events"
  }
];

// 活動數據
const events = [
  {
    id: 1,
    title: "2023年度行業發展趨勢研討會",
    date: "2023年5月15日",
    description: "邀請行業專家分享對未來發展趨勢的見解和分析，探討行業面臨的機遇與挑戰。",
    image: "/event-1.jpg"
  },
  {
    id: 2,
    title: "會員交流晚宴",
    date: "2023年6月20日",
    description: "為會員提供社交和商業合作的機會，促進會員之間的交流與協作。",
    image: "/event-2.jpg"
  },
  {
    id: 3,
    title: "專業技能提升工作坊",
    date: "2023年7月10日",
    description: "通過實踐性的工作坊幫助會員提升專業技能，跟上行業發展步伐。",
    image: "/event-3.jpg"
  }
];

// 輪播圖控制
const currentSlide = ref(0);
let slideInterval = null;

const startSlideShow = () => {
  slideInterval = setInterval(() => {
    currentSlide.value = (currentSlide.value + 1) % slides.length;
  }, 5000);
};

onMounted(() => {
  startSlideShow();
});

onUnmounted(() => {
  clearInterval(slideInterval);
});
</script> 