<template>
  <v-list v-for="(skillItem, skillIndex) in skillList" :key="`skill-${skillIndex}`" width="60vw">
    <v-list-subheader>{{ skillItem.title }}</v-list-subheader>
    
    <template v-if="skillItem.children && skillItem.children.length > 0">
      <v-list-item v-for="(skillSubItem, skillSubIndex) in skillItem.children" :key="`skill-${skillIndex}-${skillSubIndex}`" :value="skillSubItem" color="primary">
        <template v-slot:prepend>
          <v-icon :icon="skillSubItem.icon"></v-icon>
        </template>
        <v-list-item-title v-text="skillSubItem.text"></v-list-item-title>
      </v-list-item>
    </template>
  </v-list>
</template>

<script setup lang="ts">
const items: {text: string; icon: string }[] =  [
  { text: 'Real-Time', icon: 'mdi-clock' },
  { text: 'Audience', icon: 'mdi-account' },
  { text: 'Conversions', icon: 'mdi-flag' },
]

const skillList: {title: string, children: {text: string; icon: string; description?: string }[]}[] = [
  {
    title: 'Frontend Tech Stack',
    children: [
      { text: 'JavaScript ES6', icon: 'mdi-language-javascript'},
      { text: 'TypeScript', icon: 'mdi-language-typescript'},
      { text: 'Vue 2', icon: 'mdi-vuejs', description: '包含 Vue Composition api 以及 options 寫法都碰過'},
      { text: 'Vue 3', icon: 'mdi-vuejs'},
      { text: 'Nuxt 2', icon: 'mdi-nuxt', description: '包含 Nuxt Composition api'},
      { text: 'Nuxt 3', icon: 'mdi-nuxt'},
      { text: 'HTML', icon: 'mdi-language-html5'},
      { text: 'CSS', icon: 'mdi-language-css3'},
      { text: 'JQuery', icon: 'mdi-jquery'}
    ]
  },
  {
    title: 'Others',
    children: [
      { text: 'Git', icon: 'mdi-git'},
    ]
  }
]
</script>