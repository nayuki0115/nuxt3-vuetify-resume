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
      <v-btn variant="outlined" color="orange" @click="resumeWeb('Linkedin')" prepend-icon="mdi-linkedin">Linkedin</v-btn>
      <v-btn variant="outlined" color="orange" @click="resumeWeb('Github')" prepend-icon="mdi-github">Github</v-btn>
      <v-btn variant="outlined" color="orange" @click="resumeWeb('CakeResume')" prepend-icon="mdi-file-account">CakeResume</v-btn>
    </v-card-actions>


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
}
const introductionGroup:introductionItem  = {
  cName: '吳冠儀',
  eName: 'Annie Wu',
  cJob: '前端工程師',
  eJob: 'Frontend Engineer',
  email: 'annie25506@gmail.com',
  locate: 'Taipei, Taiwan'
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
  // switch (key) {
  //   case value:
      
  //     break;
  
  //   default:
  //     break;
  // }
}


</script>



