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
      <v-card-title>{{ `${introductionGroup.cName} ${introductionGroup.eName}` }}</v-card-title>
    </v-img>

    <v-card-subtitle class="pt-4">
      {{ `${introductionGroup.cJob} ${introductionGroup.eJob}` }}
    </v-card-subtitle>

    <v-card-text>
      <div>{{ introductionGroup.email }}</div>
      <div><v-icon :icon="'mdi-map-marker'"></v-icon> {{ introductionGroup.locate }}</div>
    </v-card-text>

    <v-card-text class="text">

    </v-card-text>

    <v-card-actions>
      <v-btn color="orange">
        Share
      </v-btn>

      <v-btn color="orange">
        Explore
      </v-btn>
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

</script>



