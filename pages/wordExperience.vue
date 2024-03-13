<template>
  <v-timeline align="start">
    <v-timeline-item
      v-for="(item, i) in wordList"
      :key="i"
      :dot-color="item.color"
      :icon="item.icon"
      fill-dot
    >
      <v-card hover :href="item.link" rel="noopener" target="_blank" :append-icon="`${ item.link ? 'mdi-open-in-new' : ''}`" :class="['text-h6', `bg-${item.color}`]">
        <template v-slot:title>
          {{ `${item.title}` }}
        </template>
        <v-card-text class="bg-white text--primary">
          <v-chip class="ma-2" v-for="(techItem, techIndex) in item.useTech" :key="`skill-${techIndex}`" :prepend-icon="`${techItem.icon}`" >
            {{ `${techItem.name}` }}
          </v-chip>
          <ul class="description-style">
            <li v-for="(textItem, textIndex) in item.description" :key="`text-${textIndex}`">{{ textItem }}</li>
          </ul>

        </v-card-text>
      </v-card>
    </v-timeline-item>
  </v-timeline>
</template>
<script setup lang="ts">
interface wordListItem {
  color: string;
  icon: string;
  title: string;
  description: string[];
  useTech: {
    name: string; 
    icon: string;
  }[];
  link?: string;
}

const wordList: wordListItem[]  = [
  {
    color: 'red-lighten-2',
    icon: 'mdi-star',
    title: '桃園市儀表版',
    useTech: [
      { name: 'Nuxt 3', icon: 'mdi-nuxt'},
      { name: 'Vue 3', icon: 'mdi-vuejs'}
    ],
    description: ['建置前台，功能以圖表呈現為主，也會有圖表和圖表間的連動','首次使用 Nuxt 3 的專案', '擔任此專案 RDL ( RD Leader ) ，負責與pm溝通、分配RD工作']
  },
  {
    color: 'pink-lighten-2',
    icon: 'mdi-book-variant',
    title: '某電商改版',
    useTech: [
      { name: 'Nuxt 2 ( Nuxt Composition api )', icon: 'mdi-nuxt'},
      { name: 'Vue 2 ( Vue Composition api )', icon: 'mdi-vuejs'}
    ],
    description: ['實作前後台前端商品相關功能、購物車功能', 'GTM 介接、i18n', '擔任此專案 RDL ( RD Leader ) ，負責與pm溝通、分配RD工作 ']
  },
  {
    color: 'purple-lighten-2',
    icon: 'mdi-airballoon',
    title: '桃園市立大溪木藝生態博物館  大溪學文化資源網',
    useTech: [
      { name: 'Nuxt 2 ( Nuxt Composition api )', icon: 'mdi-nuxt'},
      { name: 'Vue 2 ( Vue Composition api )', icon: 'mdi-vuejs'}
    ],
    description: ['此為新建系統(沒有舊系統)，各個分類都有大量的欄位資料。在上稿之前也需設計審核流程，主題專區設計共有接近20來個元件，供使用者編輯。', '擔任此專案的 RDL ( RD Leader ) ，負責與pm溝通、分配RD工作', '通過無障礙 AA', '前後台系統'],
    link: 'https://daxiculture.tycg.gov.tw/'
  },
  {
    color: 'blue-lighten-2',
    icon: 'mdi-layers-triple',
    title: '國立臺灣歷史博物館 影音資料庫',
    useTech:  [
      { name: 'Nuxt 2 ( Nuxt Composition api )', icon: 'mdi-nuxt'},
      { name: 'Vue 2 ( Vue Composition api )', icon: 'mdi-vuejs'}
    ],
    description: ['此專案有舊系統，需介接文化部影音平台，但因回傳速度問題，影片縮圖的檢視會有延遲，盡量減少使用者等待時間過長。', '擔任此專案的 RDL ( RD Leader ) ，負責與pm溝通、分配RD工作', '前後台系統，實作各個詮釋資料欄位編輯、呈現 ，包含影音播放', '通過無障礙 AA'],
    link: 'https://film.nmth.gov.tw/'
  },
  {
    color: 'indigo-lighten-2',
    icon: 'mdi-book-alert',
    title: '國立臺灣歷史博物館 近代臺灣報刊資料庫',
    useTech:  [
      { name: 'Nuxt 2 ', icon: 'mdi-nuxt'},
      { name: 'Vue 2 ', icon: 'mdi-vuejs'}
    ],
    description: ['負責前、後台介接', '前台有圖片有框定需求', '通過無障礙 AA'],
    link: 'https://newspaper.nmth.gov.tw/'
  },
  {
    color: 'deep-purple-lighten-2',
    icon: 'mdi-school',
    title: '國立臺灣歷史博物館 校園生活記憶庫',
    useTech:  [
      { name: 'Nuxt 2 ', icon: 'mdi-nuxt'},
      { name: 'Vue 2 ', icon: 'mdi-vuejs'}
    ],
    description: ['此專案有舊系統，擁有大量圖檔以及詮釋資料，也提供不同的檢視方式，供使用者使用。', '前台有圖片有框定需求', '通過無障礙 AA', '地圖 leftlet、圖表 E-charts'],
    link: 'https://school.nmth.gov.tw/'
  },
  {
    color: 'teal-lighten-2',
    icon: 'mdi-file-alert-outline',
    title: '國家人權博物館 檔案資訊系統暨資料庫建置計畫',
    useTech:  [
      { name: 'Nuxt 2 ', icon: 'mdi-nuxt'},
      { name: 'Vue 2 ', icon: 'mdi-vuejs'}
    ],
    description: ['此專案為新建系統，需特別注意資料之間有層級性的問題。也有典藏系統之審核流程，提供浮水印編輯模組，此為自己手刻', '擔任此專案的 RDL (RD Leader) ，負責與pm溝通、分配RD工作', '圖片編輯套件改寫', '浮水印編輯模組'],
    link: 'https://hras.nhrm.gov.tw/'
  },
  {
    color: 'cyan-lighten-2',
    icon: 'mdi-tree',
    title: '羅東林管處 蘭陽地區林業文化歷史檔案保存整合系統建置計畫',
    useTech:  [
      { name: 'Vue 2 ', icon: 'mdi-vuejs'}
    ],
    description: ['負責前、後台介接', 'Chart.js'],
    link: 'https://luodongarchives.forest.gov.tw/'
  },
  {
    color: 'light-blue-lighten-2',
    icon: 'mdi-food-apple',
    title: '灃食飲食 灃食飲食常識庫',
    useTech:  [
      { name: 'Vue 2 ', icon: 'mdi-vuejs'}
    ],
    description: ['負責圖表介接、所有新聞介接']
  },
  {
    color: 'green-lighten-2',
    icon: 'mdi-information-outline ',
    title: '經濟部標準檢驗局 知識管理入口網',
    useTech: [
      { name: 'jQuery', icon: 'mdi-jquery'}
    ],
    description: ['負責首頁、所有知識文件介接、帳號權限...等', 'gridstack(版塊拖曳)']
  },
  {
    color: 'light-green-lighten-2',
    icon: 'mdi-search-web',
    title: '國立臺灣歷史博物館 研究資源管理系統',
    useTech: [
      { name: 'jQuery', icon: 'mdi-jquery'}
    ],
    description: ['負責刻版(使用bootstrap)、部分模組介接', '影片播放套件、圖片剪裁套件改寫']
  },
  {
    color: 'lime-lighten-2',
    icon: 'mdi-book-open-blank-variant-outline',
    title: '文化部 國家漫畫史料調查研究及數位典藏計畫',
    useTech: [
      { name: 'jQuery', icon: 'mdi-jquery'}
    ],
    description: ['負責後台部分模組介接']
  },
  {
    color: 'orange-lighten-2',
    icon: 'mdi-api',
    title: '臺北市政府 資料開放平台',
    useTech: [
      { name: 'jQuery', icon: 'mdi-jquery'}
    ],
    description: ['負責開放資料介接、圖片介接', 'E-Chart、Blade、bootstrap'], 
    link: 'https://data.taipei/#/'
  },
  {
    color: 'amber-lighten-2',
    icon: 'mdi-account',
    title: '臺北市議會 新聞知識系統',
    useTech: [
      { name: 'jQuery', icon: 'mdi-jquery'}
    ],
    description: ['進公司後第一個專案，使用JQeury 混合著 Blade，有不少權限控管處理', '使用 Bootstrap、E-Chart'],
    link: 'https://news.tcc.gov.tw'
  }
]
</script>

<style lang="scss" scoped>
.description-style {
  padding: 0 0 0 1rem;
}
</style>