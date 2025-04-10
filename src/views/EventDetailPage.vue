<template>
  <div>
    <div v-if="loading" class="py-32 text-center">
      <div class="inline-block h-12 w-12 border-4 border-blue-600 border-t-transparent rounded-full animate-spin"></div>
      <p class="mt-4 text-gray-600">載入中...</p>
    </div>
    
    <div v-else-if="event" class="pb-16">
      <!-- 活動頭部資訊 -->
      <section class="bg-blue-800 text-white pt-24 pb-16">
        <div class="container-custom">
          <div class="flex items-center text-blue-200 mb-4">
            <router-link to="/events" class="flex items-center hover:text-white transition-colors">
              <svg class="w-5 h-5 mr-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
              </svg>
              返回活動列表
            </router-link>
          </div>
          
          <div class="grid grid-cols-1 md:grid-cols-12 gap-8 items-center">
            <div class="md:col-span-8">
              <div class="flex flex-wrap gap-2 mb-4">
                <span class="px-3 py-1 text-sm bg-blue-700 text-white rounded-full">{{ event.type }}</span>
                <span :class="['px-3 py-1 text-sm rounded-full', getStatusBadgeClass(event.status)]">{{ event.status }}</span>
              </div>
              <h1 class="text-3xl md:text-4xl font-bold mb-4">{{ event.title }}</h1>
              <div class="flex flex-wrap text-blue-100 mb-6">
                <div class="flex items-center mr-6 mb-2">
                  <svg class="w-5 h-5 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
                  </svg>
                  <span>{{ event.date }}</span>
                </div>
                <div class="flex items-center mr-6 mb-2">
                  <svg class="w-5 h-5 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>{{ event.time }}</span>
                </div>
                <div class="flex items-center mb-2">
                  <svg class="w-5 h-5 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                  </svg>
                  <span>{{ event.location }}</span>
                </div>
              </div>
              <p class="text-lg">{{ event.description }}</p>
            </div>
            <div class="md:col-span-4">
              <div v-if="event.status === '報名中'" class="bg-white text-gray-800 p-6 rounded-lg shadow-md">
                <h3 class="text-xl font-bold mb-4">活動報名</h3>
                <p class="text-gray-600 mb-4">立即報名參加本次活動，名額有限，請儘早報名！</p>
                <button class="btn btn-primary w-full py-3">立即報名</button>
              </div>
              <div v-else-if="event.status === '籌備中'" class="bg-white text-gray-800 p-6 rounded-lg shadow-md">
                <h3 class="text-xl font-bold mb-4">活動籌備中</h3>
                <p class="text-gray-600 mb-4">活動正在籌備中，敬請期待...</p>
                <button class="btn btn-secondary w-full py-3">預約提醒</button>
              </div>
              <div v-else class="bg-white text-gray-800 p-6 rounded-lg shadow-md">
                <h3 class="text-xl font-bold mb-4">活動已結束</h3>
                <p class="text-gray-600 mb-4">感謝您的關注，活動已結束。</p>
                <button class="btn btn-secondary w-full py-3">查看活動回顧</button>
              </div>
            </div>
          </div>
        </div>
      </section>
      
      <!-- 活動詳情內容 -->
      <section class="py-16 bg-white">
        <div class="container-custom">
          <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div class="md:col-span-2">
              <h2 class="text-2xl font-bold text-gray-800 mb-6">活動詳情</h2>
              
              <!-- 活動圖片 -->
              <div class="mb-8">
                <img :src="event.image" :alt="event.title" class="w-full h-auto rounded-lg shadow-md">
              </div>
              
              <!-- 活動詳細介紹 -->
              <div class="prose max-w-none">
                <h3>活動背景</h3>
                <p>
                  隨著行業的不斷發展和變革，企業面臨著越來越多的挑戰和機遇。為了幫助會員企業更好地了解行業趨勢，把握發展方向，我們特別舉辦本次活動，邀請行業內知名專家和企業領袖分享他們的見解和經驗。
                </p>
                
                <h3>活動亮點</h3>
                <ul>
                  <li>權威專家分享行業最新趨勢和發展方向</li>
                  <li>案例分析，解讀成功企業的創新策略</li>
                  <li>互動討論，解答企業在發展中遇到的實際問題</li>
                  <li>社交環節，拓展人脈，尋找合作機會</li>
                </ul>
                
                <h3>議程安排</h3>
                <div class="border-l-4 border-blue-600 pl-4 my-4 space-y-4">
                  <div>
                    <h4 class="font-bold">13:30 - 14:00</h4>
                    <p>簽到</p>
                  </div>
                  <div>
                    <h4 class="font-bold">14:00 - 14:15</h4>
                    <p>開場致辭 - 協會理事長</p>
                  </div>
                  <div>
                    <h4 class="font-bold">14:15 - 15:00</h4>
                    <p>主題演講一：《行業發展新趨勢》- XX專家</p>
                  </div>
                  <div>
                    <h4 class="font-bold">15:00 - 15:45</h4>
                    <p>主題演講二：《創新驅動發展》- XX企業CEO</p>
                  </div>
                  <div>
                    <h4 class="font-bold">15:45 - 16:00</h4>
                    <p>茶歇</p>
                  </div>
                  <div>
                    <h4 class="font-bold">16:00 - 16:45</h4>
                    <p>圓桌討論：《面向未來的企業戰略》</p>
                  </div>
                  <div>
                    <h4 class="font-bold">16:45 - 17:00</h4>
                    <p>提問環節</p>
                  </div>
                  <div>
                    <h4 class="font-bold">17:00 - 17:30</h4>
                    <p>交流與社交</p>
                  </div>
                </div>
                
                <h3>參與對象</h3>
                <p>
                  本次活動面向協會會員企業的高管、決策者和相關領域的專業人士開放。非會員企業如希望參加，請提前聯繫協會秘書處。
                </p>
                
                <h3>參與方式</h3>
                <p>
                  請點擊右側"立即報名"按鈕填寫報名資訊，或致電協會秘書處進行報名。報名成功後，我們將通過郵件發送活動確認函和詳細參會指南。
                </p>
              </div>
            </div>
            
            <!-- 側邊欄 -->
            <div>
              <div class="sticky top-8">
                <!-- 分享 -->
                <div class="bg-gray-50 p-6 rounded-lg mb-6">
                  <h3 class="text-lg font-semibold text-gray-800 mb-4">分享活動</h3>
                  <div class="flex space-x-4">
                    <a href="#" class="bg-gray-200 p-2 rounded-full hover:bg-blue-100 hover:text-blue-600 transition-colors">
                      <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M22.675 0h-21.35c-.732 0-1.325.593-1.325 1.325v21.351c0 .731.593 1.324 1.325 1.324h11.495v-9.294h-3.128v-3.622h3.128v-2.671c0-3.1 1.893-4.788 4.659-4.788 1.325 0 2.463.099 2.795.143v3.24l-1.918.001c-1.504 0-1.795.715-1.795 1.763v2.313h3.587l-.467 3.622h-3.12v9.293h6.116c.73 0 1.323-.593 1.323-1.325v-21.35c0-.732-.593-1.325-1.325-1.325z" />
                      </svg>
                    </a>
                    <a href="#" class="bg-gray-200 p-2 rounded-full hover:bg-blue-100 hover:text-blue-600 transition-colors">
                      <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z" />
                      </svg>
                    </a>
                    <a href="#" class="bg-gray-200 p-2 rounded-full hover:bg-blue-100 hover:text-blue-600 transition-colors">
                      <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
                      </svg>
                    </a>
                    <a href="#" class="bg-gray-200 p-2 rounded-full hover:bg-blue-100 hover:text-blue-600 transition-colors">
                      <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z" />
                      </svg>
                    </a>
                  </div>
                </div>
                
                <!-- 聯繫方式 -->
                <div class="bg-gray-50 p-6 rounded-lg">
                  <h3 class="text-lg font-semibold text-gray-800 mb-4">聯繫方式</h3>
                  <div class="space-y-3">
                    <div class="flex items-start">
                      <svg class="w-5 h-5 text-gray-600 mt-1 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 12a4 4 0 10-8 0 4 4 0 008 0zm0 0v1.5a2.5 2.5 0 005 0V12a9 9 0 10-9 9m4.5-1.206a8.959 8.959 0 01-4.5 1.207" />
                      </svg>
                      <span class="text-gray-700">activites@association.org</span>
                    </div>
                    <div class="flex items-start">
                      <svg class="w-5 h-5 text-gray-600 mt-1 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                      </svg>
                      <span class="text-gray-700">(+86) 10-12345678</span>
                    </div>
                    <div class="flex items-start">
                      <svg class="w-5 h-5 text-gray-600 mt-1 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
                      </svg>
                      <span class="text-gray-700">李女士 (活動專員)</span>
                    </div>
                  </div>
                </div>
                
                <!-- 相關活動 -->
                <div class="mt-6">
                  <h3 class="text-lg font-semibold text-gray-800 mb-4">相關活動</h3>
                  <div class="space-y-4">
                    <div v-for="(relatedEvent, index) in relatedEvents" :key="index" class="bg-gray-50 p-4 rounded-lg">
                      <div class="text-sm text-gray-500 mb-1">{{ relatedEvent.date }}</div>
                      <h4 class="font-medium text-gray-800 mb-1">{{ relatedEvent.title }}</h4>
                      <router-link :to="`/events/${relatedEvent.id}`" class="text-blue-600 text-sm hover:text-blue-800">
                        查看詳情
                      </router-link>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
    
    <div v-else class="py-32 text-center">
      <svg class="mx-auto h-16 w-16 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.172 16.172a4 4 0 015.656 0M9 10h.01M15 10h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
      </svg>
      <h2 class="mt-4 text-2xl font-bold text-gray-700">未找到活動</h2>
      <p class="mt-2 text-gray-500">抱歉，未找到您請求的活動信息</p>
      <div class="mt-6">
        <router-link to="/events" class="btn btn-primary">
          返回活動列表
        </router-link>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute();
const eventId = route.params.id;

const loading = ref(true);
const event = ref(null);

// 模拟从后端获取活动数据
const fetchEvent = () => {
  // 这里实际应用中应该调用API获取数据
  // 这里使用模拟数据
  const eventsData = [
    {
      id: '1',
      title: '2025年度行业发展趋势研讨会',
      type: '研讨会',
      date: '2025年5月15日',
      time: '14:00-17:00',
      location: '北京国际会议中心',
      description: '邀请行业专家分享对未来发展趋势的见解和分析，探讨行业面临的机遇与挑战。',
      image: '/event-1.jpg',
      status: '报名中'
    },
    {
      id: '2',
      title: '会员交流晚宴',
      type: '交流晚宴',
      date: '2025年6月20日',
      time: '18:30-21:00',
      location: '上海XX大酒店',
      description: '为会员提供社交和商业合作的机会，促进会员之间的交流与协作。',
      image: '/event-2.jpg',
      status: '筹备中'
    },
    {
      id: '3',
      title: '专业技能提升工作坊',
      type: '培训课程',
      date: '2025年7月10日',
      time: '09:00-17:00',
      location: '线上直播',
      description: '通过实践性的工作坊帮助会员提升专业技能，跟上行业发展步伐。',
      image: '/event-3.jpg',
      status: '报名中'
    }
  ];
  
  // 模拟API延迟
  setTimeout(() => {
    const foundEvent = eventsData.find(e => e.id === eventId);
    event.value = foundEvent || null;
    loading.value = false;
  }, 800);
};

// 相关活动数据
const relatedEvents = [
  {
    id: '4',
    title: '2024年第四季度行业论坛',
    date: '2024年12月5日'
  },
  {
    id: '5',
    title: '先进制造企业参观考察',
    date: '2025年4月25日'
  },
  {
    id: '6',
    title: '数字化转型专题培训',
    date: '2024年11月15日'
  }
];

// 状态徽章样式
const getStatusBadgeClass = (status) => {
  switch (status) {
    case '报名中':
      return 'bg-green-600 text-white';
    case '筹备中':
      return 'bg-yellow-600 text-white';
    case '已结束':
      return 'bg-gray-600 text-white';
    default:
      return 'bg-gray-600 text-white';
  }
};

onMounted(() => {
  fetchEvent();
});
</script> 