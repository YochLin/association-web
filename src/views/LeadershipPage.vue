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
              <h3 class="text-2xl font-bold text-gray-800 mb-2">蔡思庭</h3>
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
        
        <!-- 秘書長 -->
        <div class="mb-16">
          <div class="flex flex-col md:flex-row items-center gap-8 max-w-4xl mx-auto">
            <div class="w-48 h-48 overflow-hidden rounded-full border-4 border-blue-100 shadow-lg flex-shrink-0">
              <img src="/secretary.jpg" alt="秘書長" class="w-full h-full object-cover">
            </div>
            <div>
              <h3 class="text-xl font-bold text-gray-800 mb-2">蕭雅梅</h3>
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
            <p class="text-blue-600 font-medium mb-2">{{ chairman.term }}</p>
            <p class="text-gray-600 text-sm mb-2">{{ chairman.period }}</p>
            <p class="text-gray-600 text-sm">{{ chairman.company }}</p>
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
  { name: '張廷章', term: '創會會長', period: '2000-2004', company: '巨森食品企業有限公司', image: '/past-chairman-1.jpg' },
  { name: '林坤炎', term: '榮譽理事長', period: '2000-2004', company: '巨森食品企業有限公司', image: '/past-chairman-1.jpg' },
  { name: '徐倉賓', term: '第一屆副理事長', period: '2000-2004', company: '弘爺國際企業股份有限公司', image: '/past-chairman-1.jpg' },
  { name: '蔡澔鎔', term: '第二屆理事長', period: '2004-2008', company: '齋聖彥有限公司', image: '/past-chairman-2.jpg' },
  { name: '陳筑怜', term: '第二屆理事長', period: '2004-2008', company: '齋聖彥有限公司', image: '/past-chairman-2.jpg' },
  { name: '葉益芳', term: '第三屆理事長', period: '2008-2015', company: '益方封口機公司', image: '/past-chairman-3.jpg' },
  { name: '林良田', term: '第五,六屆理事長', period: '2008-2015', company: '板田實業有限公司', image: '/past-chairman-3.jpg' },
  { name: '陳弘欽', term: '第七,八屆理事長', period: '2008-2015', company: '巧沛國際股份有限公司', image: '/past-chairman-3.jpg' },
  { name: '莊茂山', term: '第九屆理事長', period: '2008-2015', company: '吉得堡食品有限公司', image: '/past-chairman-3.jpg' },
];
</script> 