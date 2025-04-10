<template>
  <div>
    <!-- 頁面標題部分 -->
    <section class="bg-blue-800 text-white py-20">
      <div class="container-custom text-center">
        <h1 class="text-4xl md:text-5xl font-bold mb-4">協會領導</h1>
        <p class="text-xl md:text-2xl max-w-3xl mx-auto">了解協會領導團隊，共同推動行業發展</p>
      </div>
    </section>

    <!-- 當屆理事會領導 -->
    <section class="py-16 bg-white">
      <div class="container-custom">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold text-gray-800 mb-4">本屆理事會</h2>
          <div class="w-20 h-1 bg-blue-600 mx-auto mb-4"></div>
          <p class="text-gray-600 max-w-2xl mx-auto">
            第五屆理事會成員由行業內著名企業領導和專業人士組成，任期2023年至2027年
          </p>
        </div>
        
        <!-- 理事長 -->
        <div class="mb-16">
          <div class="flex flex-col md:flex-row items-center gap-8 max-w-4xl mx-auto">
            <div class="w-64 h-64 overflow-hidden rounded-full border-4 border-blue-100 shadow-lg flex-shrink-0">
              <img src="/chairman.jpg" alt="理事長" class="w-full h-full object-cover">
            </div>
            <div>
              <h3 class="text-2xl font-bold text-gray-800 mb-2">張偉明</h3>
              <p class="text-blue-600 font-medium mb-4">理事長</p>
              <p class="text-gray-600 mb-4 leading-relaxed">
                張偉明先生現任XX集團有限公司董事長，在行業內擁有超過30年的豐富經驗。他於2023年當選為協會第五屆理事長，致力於推動行業技術創新和國際化發展。
              </p>
              <p class="text-gray-600 leading-relaxed">
                在他的領導下，協會積極推動行業標準制定，促進企業間合作，為行業持續健康發展作出重要貢獻。
              </p>
            </div>
          </div>
        </div>
        
        <!-- 副理事長 -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-16">
          <div class="card p-6 flex flex-col sm:flex-row gap-6">
            <div class="w-32 h-32 rounded-full overflow-hidden border-4 border-blue-100 flex-shrink-0 mx-auto sm:mx-0">
              <img src="/vice-chairman-1.jpg" alt="副理事長" class="w-full h-full object-cover">
            </div>
            <div>
              <h3 class="text-xl font-bold text-gray-800 mb-1 text-center sm:text-left">李紅梅</h3>
              <p class="text-blue-600 font-medium mb-3 text-center sm:text-left">副理事長</p>
              <p class="text-gray-600 leading-relaxed">
                李紅梅女士現任YY科技有限公司CEO，負責協會國際合作和行業標準委員會工作。
              </p>
            </div>
          </div>
          
          <div class="card p-6 flex flex-col sm:flex-row gap-6">
            <div class="w-32 h-32 rounded-full overflow-hidden border-4 border-blue-100 flex-shrink-0 mx-auto sm:mx-0">
              <img src="/vice-chairman-2.jpg" alt="副理事長" class="w-full h-full object-cover">
            </div>
            <div>
              <h3 class="text-xl font-bold text-gray-800 mb-1 text-center sm:text-left">王建國</h3>
              <p class="text-blue-600 font-medium mb-3 text-center sm:text-left">副理事長</p>
              <p class="text-gray-600 leading-relaxed">
                王建國先生現任ZZ實業集團總裁，負責協會會員發展和行業培訓工作。
              </p>
            </div>
          </div>
        </div>
        
        <!-- 秘書長 -->
        <div class="mb-16">
          <div class="flex flex-col md:flex-row items-center gap-8 max-w-4xl mx-auto">
            <div class="w-48 h-48 overflow-hidden rounded-full border-4 border-blue-100 shadow-lg flex-shrink-0">
              <img src="/secretary.jpg" alt="秘書長" class="w-full h-full object-cover">
            </div>
            <div>
              <h3 class="text-xl font-bold text-gray-800 mb-2">劉明</h3>
              <p class="text-blue-600 font-medium mb-4">秘書長</p>
              <p class="text-gray-600 leading-relaxed">
                劉明先生自2015年起擔任協會秘書長，全面負責協會日常運營管理工作。他擁有豐富的協會管理經驗，致力於提升協會服務質量，推動協會各項工作的開展和實施。
              </p>
            </div>
          </div>
        </div>
        
        <!-- 理事會成員 -->
        <div>
          <h3 class="text-xl font-semibold text-gray-800 mb-6 text-center">理事會成員</h3>
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-6">
            <div v-for="(member, index) in boardMembers" :key="index" class="text-center">
              <div class="w-24 h-24 rounded-full overflow-hidden border-2 border-blue-100 mx-auto mb-3">
                <img :src="member.image" :alt="member.name" class="w-full h-full object-cover">
              </div>
              <h4 class="font-medium text-gray-800">{{ member.name }}</h4>
              <p class="text-sm text-gray-600">{{ member.company }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 歷屆理事長部分 -->
    <section class="py-16 bg-gray-50">
      <div class="container-custom">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold text-gray-800 mb-4">歷屆理事長</h2>
          <div class="w-20 h-1 bg-blue-600 mx-auto mb-4"></div>
          <p class="text-gray-600 max-w-2xl mx-auto">
            感謝歷屆理事長為協會發展做出的重要貢獻
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div v-for="(chairman, index) in pastChairmen" :key="index" class="card p-6 text-center">
            <div class="w-32 h-32 rounded-full overflow-hidden border-4 border-blue-100 mx-auto mb-4">
              <img :src="chairman.image" :alt="chairman.name" class="w-full h-full object-cover">
            </div>
            <h3 class="text-lg font-bold text-gray-800">{{ chairman.name }}</h3>
            <p class="text-blue-600 font-medium mb-2">第{{ chairman.term }}屆理事長</p>
            <p class="text-gray-600 text-sm mb-2">{{ chairman.period }}</p>
            <p class="text-gray-600 text-sm">{{ chairman.company }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 秘書處部分 -->
    <section class="py-16 bg-white">
      <div class="container-custom">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold text-gray-800 mb-4">秘書處</h2>
          <div class="w-20 h-1 bg-blue-600 mx-auto mb-4"></div>
          <p class="text-gray-600 max-w-2xl mx-auto">
            秘書處負責協會日常工作的組織和實施
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="(staff, index) in secretariat" :key="index" class="card p-6 text-center">
            <div class="w-24 h-24 rounded-full overflow-hidden border-2 border-blue-100 mx-auto mb-3">
              <img :src="staff.image" :alt="staff.name" class="w-full h-full object-cover">
            </div>
            <h3 class="text-lg font-bold text-gray-800 mb-1">{{ staff.name }}</h3>
            <p class="text-blue-600 font-medium mb-3">{{ staff.position }}</p>
            <p class="text-gray-600 text-sm">{{ staff.responsibility }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
// 理事會成員數據
const boardMembers = [
  { name: '陳志強', company: 'AA公司', image: '/board-1.jpg' },
  { name: '張麗華', company: 'BB集團', image: '/board-2.jpg' },
  { name: '王偉', company: 'CC科技', image: '/board-3.jpg' },
  { name: '李小紅', company: 'DD傳媒', image: '/board-4.jpg' },
  { name: '趙明', company: 'EE工業', image: '/board-5.jpg' },
  { name: '黃海', company: 'FF商貿', image: '/board-6.jpg' },
  { name: '周健', company: 'GG實業', image: '/board-7.jpg' },
  { name: '吳芳', company: 'HH投資', image: '/board-8.jpg' },
];

// 歷屆理事長數據
const pastChairmen = [
  { name: '陳大明', term: '一', period: '2000-2004', company: 'XX集團創始人', image: '/past-chairman-1.jpg' },
  { name: '李建華', term: '二', period: '2004-2008', company: 'YY科技前CEO', image: '/past-chairman-2.jpg' },
  { name: '王強', term: '三', period: '2008-2015', company: 'ZZ實業董事長', image: '/past-chairman-3.jpg' },
  { name: '錢路明', term: '四', period: '2015-2023', company: 'WW控股集團主席', image: '/past-chairman-4.jpg' },
];

// 秘書處成員數據
const secretariat = [
  { 
    name: '劉明', 
    position: '秘書長', 
    responsibility: '全面負責協會日常運營管理',
    image: '/secretary.jpg'
  },
  { 
    name: '張佳麗', 
    position: '副秘書長', 
    responsibility: '負責會員服務和活動組織',
    image: '/deputy-secretary-1.jpg'
  },
  { 
    name: '王小龍', 
    position: '副秘書長', 
    responsibility: '負責財務管理和對外合作',
    image: '/deputy-secretary-2.jpg'
  },
  { 
    name: '李媛', 
    position: '會員部主任', 
    responsibility: '負責會員發展與服務工作',
    image: '/staff-1.jpg'
  },
  { 
    name: '趙鑫', 
    position: '活動部主任', 
    responsibility: '負責協會各類活動的策劃與實施',
    image: '/staff-2.jpg'
  },
  { 
    name: '黃志強', 
    position: '宣傳部主任', 
    responsibility: '負責協會品牌宣傳與媒體合作',
    image: '/staff-3.jpg'
  },
];
</script> 