<template>
  <v-app>
    <v-app-bar :elevation="2" rounded>
      <v-container class="mx-auto d-flex align-center justify-center">
        <v-avatar
          class="me-4 "
          color="grey-darken-1"
          size="32"
          image="@/assets/images/avatar.jpg"
        ></v-avatar>

        <v-app-bar-title >Annie Wu</v-app-bar-title>

        <v-btn
          v-for="(link, index) in links"
          :key="`link-${index}`"
          :text="link"
          variant="text"
          @click="handleLinks(link)"
        ></v-btn>

        <v-spacer></v-spacer>

      </v-container>

    </v-app-bar>

    <v-main class="bg-grey-lighten-3">
      <v-container>
        <v-row>
          <v-col>
            <v-sheet
              min-height="70vh"
              rounded="lg"
              :elevation="3"
            >
            <slot />
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>

  </v-app>
</template>

<script setup lang="ts">
const route = useRoute()
useHead({
  meta: [
    { property: 'title', content: `Annie Wu Resume` },
    { property: 'og:title', content: `Annie Wu Resume` }
  ]
})

const links: string[] = [
  'Introduction',
  'Skill',
  'Work Experience',
  'Book Club'
]

const router = useRouter()
const handleLinks = (link: string) => {
  switch (link) {
    case 'Introduction':
      router.push('/')
      break;
    case 'Skill':
      router.push('/skill')
      break;
    case 'Work Experience':
      router.push('/wordExperience')
      break;
      case 'Book Club':
      router.push('/bookClub')
      break;
    default:
    router.push('/')
      break;
  }
}
</script>
<style lang="scss" scoped>
.v-sheet {
  padding: 0 1rem 0 1rem;
}
</style>
