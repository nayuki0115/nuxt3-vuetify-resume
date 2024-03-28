<template>
  <v-card
    class="mx-auto"
    
  >
    <v-img
      class="align-end text-white"
      height="40vh"
      src="@/assets/images/introduction-banner.jpg"
      cover
    >
      <v-card-title class="text-h5">{{ `${introductionGroup.cName} ${introductionGroup.eName}` }}</v-card-title>
    </v-img>

    <v-card-subtitle class="pt-4 text-h6">
      {{ `${introductionGroup.cJob} ${introductionGroup.eJob}` }}
    </v-card-subtitle>

    <v-card-text class="text-subtitle-1">
      <div>{{ introductionGroup.email }}</div>
      <div><v-icon :icon="'mdi-map-marker'"></v-icon> {{ introductionGroup.locate }}</div>
    </v-card-text>

    <v-card-text class="text-subtitle-1">
      2017年碩士班畢業後，成為前端工程師已有6年 <br/>
      對前端技術與網頁設計，充滿熱忱<br/>
      在現職中已做過多個專案，想挑戰有穩定產品的職務，<br/>
      接受遠端工作、混合辦公<br/>
    </v-card-text>

    <v-card-actions>
      <v-btn variant="outlined" color="primary" @click="resumeWeb('Linkedin')" prepend-icon="mdi-linkedin">Linkedin</v-btn>
      <v-btn variant="outlined" color="black" @click="resumeWeb('Github')" prepend-icon="mdi-github">Github</v-btn>
      <v-btn variant="outlined" color="green-darken-3" @click="resumeWeb('CakeResume')" prepend-icon="mdi-file-account">CakeResume</v-btn>
    </v-card-actions>

    <v-card-subtitle class="pt-4 text-h6">學歷</v-card-subtitle>
    <v-timeline side="end" direction="horizontal">
      <v-timeline-item
        v-for="(item, index) in introductionGroup.educational"
        :key="index"
        :dot-color="item.color"
        size="small"
        min-width="30vw"
      >
        <v-alert
          :color="item.color"
          :value="true"
        >
          <div>{{ item.year }}</div>
          <div>{{ item.school }}</div>
          <div>{{ item.department }}</div>  
        
        </v-alert>
      </v-timeline-item>
    </v-timeline>

    <v-card-subtitle class="pt-4 text-h6">工作經歷</v-card-subtitle>
    <v-timeline side="end" direction="horizontal">
      <v-timeline-item
        v-for="(workItem, workIndex) in introductionGroup.work"
        :key="workIndex"
        :dot-color="workItem.color"
        size="small"
        min-width="30vw"
      >
        <v-alert
          :color="workItem.color"
          :value="true"
        >
          <div>{{ workItem.year }}</div>
          <div>{{ workItem.title }}</div>
          <div>{{ workItem.company }}</div>  
        </v-alert>
      </v-timeline-item>
    </v-timeline>

    <br/>

  </v-card>
</template>

<script setup lang="ts">
interface introductionItem {
  cName: string;
  eName: string;
  cJob: string;
  eJob: string;
  email: string;
  locate: string;
  educational: {color: string; icon?: string; year: string; school: string, department: string}[];
  work: { color: string; title: string; company: string; year: string; description: string[]}[]
}
const introductionGroup:introductionItem  = {
  cName: '吳冠儀',
  eName: 'Annie Wu',
  cJob: '前端工程師',
  eJob: 'Frontend Engineer',
  email: 'annie25506@gmail.com',
  locate: 'Taipei, Taiwan',
  educational: [
    {color: 'light-blue-lighten-5', year: '2015 - 2017', school: '國立臺北科技大學', department: '資訊與財金管理系 碩士班'},
    {color: 'light-blue-lighten-5', year: '2011 - 2015', school: '實踐大學', department: '資訊科技與管理學系 '}
  ],
  work: [
    {
      color: 'light-blue-lighten-5', title: '前端工程師(主任)',  company:'藍星球資訊股份有限公司', year: '十月 2017 - Present', 
      description: ['2017/10 擔任 前端工程師', '2019/01 升為 高級前端工程師', '2022/10 升為 主任']
    }
  ]
}

const resumeWeb = async(webType: string) => {
  let url = ''
  switch (webType) {
    case 'Linkedin':
      url = 'https://www.linkedin.com/in/nayuki0115/'
      break;
    case 'Github':
      url = 'https://github.com/nayuki0115'
      break;
    case 'CakeResume':
      url = 'https://www.cakeresume.com/nayuki0115'
      break;
    default:
      url = 'https://www.linkedin.com/in/nayuki0115/'
      break;
  }
  await navigateTo(url, {
    open: {
      target: '_blank',
    }
  })
}

</script>



