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
      Number 10
    </v-card-subtitle>

    <v-card-text>
      <div>Whitehaven Beach</div>

      <div>Whitsunday Island, Whitsunday Islands</div>
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
  eName: string
}
const introductionGroup:introductionItem  = {
  cName: '吳冠儀',
  eName: 'Annie Wu'
}

</script>



