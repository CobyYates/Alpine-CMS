<template>
  <v-row class="px-3">
    <v-col cols="4">
      <v-row v-for="detail in caseDetails" :key="detail.i" class="my-0 py-0">
        <v-col cols="4" class="px-0">
          <p class="subtitle-1">{{ detail.name }}</p>
        </v-col>
        <v-text-field
          v-if="!detail.select"
          solo
          dense
          class="my-0 py-0"
        ></v-text-field>
        <v-select
          v-if="detail.select"
          :items="detail.selects"
          solo
          dense
        ></v-select>
      </v-row>
    </v-col>
    <!--  -->
    <v-col cols="4">
      <v-tabs
        v-model="tab"
        background-color="deep-purple accent-4"
        class="elevation-2"
        dark
        :centered="centered"
        :grow="grow"
        :vertical="vertical"
        :right="right"
        :prev-icon="prevIcon ? 'mdi-arrow-left-bold-box-outline' : undefined"
        :next-icon="nextIcon ? 'mdi-arrow-right-bold-box-outline' : undefined"
        :icons-and-text="icons"
      >
        <v-tabs-slider></v-tabs-slider>

        <v-tab v-for="i in tabs" :key="i.i" :href="`#tab-${i}`">
          {{ i }}
        </v-tab>

        <v-tab-item v-for="i in tabs" :key="i.i" :value="'tab-' + i">
          <v-card flat tile>
            <div v-if="i === 'Contact Information'">
              <v-row v-for="item in tabForm[0]" :key="item.i" class="mx-3">
                <v-col cols="3">
                  <p class="subtitle-1">{{ item.name }}</p>
                </v-col>
                <v-col cols="9">
                  <v-text-field dense solo v-if="item.input"></v-text-field>
                  <v-select
                    dense
                    v-if="item.select"
                    :items="item.items"
                    solo
                  ></v-select>
                  <v-textarea
                    dense
                    solo
                    v-if="item.area"
                    height="2"
                  ></v-textarea>
                </v-col>
              </v-row>
            </div>
            <div v-if="i === 'Bill to Contact'">
              <v-row v-for="item in tabForm[1]" :key="item.i" class="mx-3">
                <v-col cols="3">
                  <p class="subtitle-1">{{ item.name }}</p>
                </v-col>
                <v-col cols="9">
                  <v-text-field dense solo v-if="item.input"></v-text-field>
                  <v-select
                    dense
                    v-if="item.select"
                    :items="item.items"
                    solo
                  ></v-select>
                  <v-textarea
                    dense
                    solo
                    v-if="item.area"
                    height="2"
                  ></v-textarea>
                </v-col>
              </v-row>
            </div>
          </v-card>
        </v-tab-item>
      </v-tabs>
    </v-col>
    <!--  -->
    <v-col cols="4" class="px-3">
      <div class="d-flex justify-space-between">
        <p class="display-1">Tasks</p>
      <center><v-btn color="primary" @click="addRow">Add New Task</v-btn></center>
      </div>
      
      <v-data-table
        dense
        :headers="headers"
        :items="clients"
        item-key="name"
        class="elevation-1"
      >
      <template v-slot:item.task="props">
        <v-edit-dialog
          :return-value.sync="props.item.task"
          @save="save"
          @cancel="cancel"
          @open="open"
          @close="close"
        > {{ props.item.task }}
          <template v-slot:input>
            <v-text-field
              v-model="props.item.task"
              label="Edit"
              single-line
              counter
            ></v-text-field>
          </template>
        </v-edit-dialog>
      </template>
      </v-data-table>
    </v-col>
  </v-row>
</template>

<script>
export default {
  methods: {
    addRow() {
      this.clients.unshift(this.newRow)
    }
  },
  data: () => ({
    tab: null,
    icons: false,
    centered: false,
    grow: false,
    vertical: false,
    prevIcon: false,
    nextIcon: false,
    right: false,
    tabs: ["Contact Information", "Bill to Contact"],
    newRow: {
        task: "task",
        assignedTo: "assigned",
        date: "date",
        estHrs: "est hrs",
        caseManager: "case manager",
        caseExpert: "case expert"
      },
    tabForm: [
      [
        {
          name: "Contact Name",
          input: true,
          select: false,
          area: false,
          icons: false
        },
        {
          name: "Company",
          input: false,
          select: true,
          area: false,
          icons: false,
          items: ["Company A", "Company B", "Company C"]
        },
        {
          name: "Email",
          input: true,
          select: false,
          area: false,
          icons: false
        },
        {
          name: "Phone",
          input: true,
          select: false,
          area: false,
          icons: false
        },
        { name: "Cell", input: true, select: false, area: false, icons: false },
        {
          name: "Comments",
          input: false,
          select: false,
          area: true,
          icons: false
        }
      ],
      [
        { name: "Name", input: true, select: false, area: false, icons: false },
        {
          name: "Email",
          input: true,
          select: false,
          area: false,
          icons: false
        },
        {
          name: "Phone",
          input: true,
          select: false,
          area: false,
          icons: false
        },
        { name: "Cell", input: true, select: false, area: false, icons: false },
        {
          name: "Comments",
          input: false,
          select: false,
          area: true,
          icons: false
        }
      ]
    ],
    caseManager: [
      "Matt",
      "Rick",
      "Troy",
      "Cory",
      "Scott",
      "Wayne",
      "Laura",
      "Jeffrey",
      "Roger",
      "James",
      "Shawn"
    ],
    caseDetails: [
      { name: "Case Name", font: "title", select: false },
      { name: "Official Case Name", font: "title", select: false },
      {
        name: "Case Manager",
        font: "subtitle-1",
        select: true,
        selects: ["Option 1", "Option 2", "Option 3"]
      },
      {
        name: "Case Expert",
        font: "subtitle-1",
        select: true,
        selects: ["Option 1", "Option 2", "Option 3"]
      },
      {
        name: "Originator",
        font: "subtitle-1",
        select: true,
        selects: ["Option 1", "Option 2", "Option 3"]
      },
      { name: "Referral", font: "subtitle-1", select: false },
      {
        name: "Stage Type",
        font: "subtitle-1",
        select: true,
        selects: ["Option 1", "Option 2", "Option 3"]
      },
      {
        name: "Stage",
        font: "subtitle-1",
        select: true,
        selects: ["Option 1", "Option 2", "Option 3"]
      },
      {
        name: "Stage Status",
        font: "subtitle-1",
        select: true,
        selects: ["Option 1", "Option 2", "Option 3"]
      },
      {
        name: "Case Type",
        font: "subtitle-1",
        select: true,
        selects: ["Option 1", "Option 2", "Option 3"]
      },
      {
        name: "Industry",
        font: "subtitle-1",
        select: true,
        selects: ["Option 1", "Option 2", "Option 3"]
      },
      {
        name: "Side",
        font: "subtitle-1",
        select: true,
        selects: ["Option 1", "Option 2", "Option 3"]
      },
      { name: "Judge", font: "subtitle-1", select: false },
      { name: "Auditor", font: "subtitle-1", select: false },
      {
        name: "State/Federal",
        font: "subtitle-1",
        select: true,
        selects: ["Option 1", "Option 2", "Option 3"]
      },
      { name: "Opposing Expert", font: "subtitle-1", select: false }
    ],
    headers: [
      {
        text: "Task",
        align: "start",
        sortable: false,
        value: "task"
      },
      { text: "Assigned To", value: "assignedTo" },
      { text: "Date", value: "date" },
      { text: "Est Hours", value: "estHrs" },
      { text: "Case Manager", value: "caseManager" },
      { text: "Case Expert", value: "caseExpert" }
    ],
    clients: [
      {
        task: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
        assignedTo: "Wylie",
        date: "5/12/2020",
        estHrs: 10,
        caseManager: "Franzen",
        caseExpert: "Martino"
      },
      {
        task: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
        assignedTo: "Lilllie",
        date: "5/12/2020",
        estHrs: 6,
        caseManager: "Kristo",
        caseExpert: "Pierre"
      },
      {
        task: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
        assignedTo: "Levin",
        date: "5/12/2020",
        estHrs: 12,
        caseManager: "Mordecai",
        caseExpert: "Lyle"
      },
      {
        task: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
        assignedTo: "Aldous",
        date: "5/12/2020",
        estHrs: 2,
        caseManager: "Inness",
        caseExpert: "Tann"
      },
      {
        task: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
        assignedTo: "Son",
        date: "5/12/2020",
        estHrs: 4,
        caseManager: "Torrin",
        caseExpert: "Torr"
      },
      {
        task: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
        assignedTo: "Harbert",
        date: "5/12/2020",
        estHrs: 3,
        caseManager: "Colan",
        caseExpert: "Dermot"
      },
    ]
  })
};
</script>

<style>
  .addRow {
    background-color: #2196F3;
    color: white;
  }
  .addRow:hover {
    background-color: white;
    color: #2196F3;
  }
</style>
