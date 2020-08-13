<template>
  <v-row align="start">
    <v-col>
      <v-data-table
        :headers="headers"
        :items="desserts"
        :items-per-page="10"
        class="elevation-1"
      ></v-data-table>
    </v-col>
    <v-btn
      absolute
      class="mx-2"
      style="right: 20px; bottom: 20px;"
      fab
      dark
      color="indigo"
    >
      <v-icon dark>mdi-plus</v-icon>
    </v-btn>
  </v-row>
</template>
<script>
export default {
  data() {
    return {
      headers: [
        { text: 'ID', value: 'id' },
        { text: 'Full Name', value: 'fullName' },
        { text: 'National ID', value: 'nationalId' },
        { text: 'Number of lands owned', value: 'numberOfLandsOwned' },
        { text: 'ownedLandsIDs', value: 'ownedLandsIDs' },
        { text: 'Owner Address', value: 'ownerAddress' },
      ],
      desserts: [
        {
          id: 'KitKat',
          fullName: 518,
          nationalId: 26.0,
          numberOfLandsOwned: 65,
          ownedLandsIDs: 7,
          ownerAddress: '6%',
        },
        {
          id: 'KitKat',
          fullName: 518,
          nationalId: 26.0,
          numberOfLandsOwned: 65,
          ownedLandsIDs: 7,
          ownerAddress: '6%',
        },
        {
          id: 'KitKat',
          fullName: 518,
          nationalId: 26.0,
          numberOfLandsOwned: 65,
          ownedLandsIDs: 7,
          ownerAddress: '6%',
        },
        {
          id: 'KitKat',
          fullName: 518,
          nationalId: 26.0,
          numberOfLandsOwned: 65,
          ownedLandsIDs: 7,
          ownerAddress: '6%',
        },
        {
          id: 'KitKat',
          fullName: 518,
          nationalId: 26.0,
          numberOfLandsOwned: 65,
          ownedLandsIDs: 7,
          ownerAddress: '6%',
        },
        {
          id: 'KitKat',
          fullName: 518,
          nationalId: 26.0,
          numberOfLandsOwned: 65,
          ownedLandsIDs: 7,
          ownerAddress: '6%',
        },
      ],
    }
  },
}
</script>

<style type="text/scss"></style>
