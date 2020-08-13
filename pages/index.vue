<template>
  <v-row align="start">
    <v-col>
      <v-data-table
        :headers="headers"
        :items="owners"
        :items-per-page="10"
        class="elevation-1"
      >
        <template v-slot:top>
          <v-toolbar flat color="white">
            <v-toolbar-title>My Owners</v-toolbar-title>
            <v-divider class="mx-4" inset vertical></v-divider>
            <v-spacer></v-spacer>
            <v-dialog v-model="dialog" max-width="500px">
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  color="primary"
                  dark
                  class="mb-2"
                  v-bind="attrs"
                  v-on="on"
                  >New Owner</v-btn
                >
              </template>
              <v-card>
                <v-card-title>
                  <span class="headline">{{ formTitle }}</span>
                </v-card-title>

                <v-card-text>
                  <v-container>
                    <v-row>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.fullName"
                          label="Owner name"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.nationalId"
                          label="National ID"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.ownerAddress"
                          label="Address"
                        ></v-text-field>
                      </v-col>
                    </v-row>
                  </v-container>
                </v-card-text>

                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn color="blue darken-1" text @click="close"
                    >Cancel</v-btn
                  >
                  <v-btn color="blue darken-1" text @click="save">Save</v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-toolbar>
        </template>
        <template v-slot:item.actions="{ item }">
          <v-icon small class="mr-2" @click="editItem(item)">
            mdi-pencil
          </v-icon>
          <v-icon small @click="deleteItem(item)">
            mdi-delete
          </v-icon>
        </template>
        <template v-slot:no-data>
          <v-btn color="primary" @click="initialize">Reset</v-btn>
        </template>
      </v-data-table>
    </v-col>
  </v-row>
</template>
<script>
export default {
  data() {
    return {
      dialog: false,
      headers: [
        { text: 'ID', value: 'id' },
        { text: 'Full Name', value: 'fullName' },
        { text: 'National ID', value: 'nationalId' },
        { text: 'Number of owners owned', value: 'numberOfOwnersOwned' },
        { text: 'ownedOwnersIDs', value: 'ownedOwnersIDs' },
        { text: 'Owner Address', value: 'ownerAddress' },
        { text: 'Actions', value: 'actions', sortable: false },
      ],
      owners: [
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
        {
          id: 518,
          fullName: 'KitKat',
          nationalId: 'Egypt',
          numberOfOwnersOwned: 65,
          ownedOwnersIDs: 7,
          ownerAddress: '6ksd flkd skl ',
        },
      ],
      editedIndex: -1,
      editedItem: {
        fullName: '',
        nationalId: '',
        numberOfOwnersOwned: 0,
        ownedOwnersIDs: '',
        ownerAddress: '',
      },
      defaultItem: {
        fullName: '',
        nationalId: '',
        numberOfOwnersOwned: 0,
        ownedOwnersIDs: '',
        ownerAddress: '',
      },
    }
  },
  computed: {
    formTitle() {
      return this.editedIndex === -1 ? 'New Owner' : 'Edit Owner'
    },
  },

  watch: {
    dialog(val) {
      val || this.close()
    },
  },
  methods: {
    editItem(item) {
      this.editedIndex = this.owners.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },

    deleteItem(item) {
      const index = this.owners.indexOf(item)
      confirm('Are you sure you want to delete this item?') &&
        this.owners.splice(index, 1)
    },

    close() {
      this.dialog = false
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      })
    },

    save() {
      if (this.editedIndex > -1) {
        Object.assign(this.owners[this.editedIndex], this.editedItem)
      } else {
        this.owners.push(this.editedItem)
      }
      this.close()
    },
  },
  head: {
    title: 'Owners',
  },
}
</script>
<style type="text/scss"></style>
