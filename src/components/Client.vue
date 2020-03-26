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
      <p class="display-1">Tasks</p>
      <v-data-table
        dense
        :headers="headers"
        :items="clients"
        item-key="name"
        class="elevation-1"
        @click:row="addRow"
      >
        <template v-slot:body.prepend="{ headers }">
          <tr @click="addRow">
            <td :colspan="headers.length">
              Add new row
            </td>
          </tr>
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
        task: null,
        contactName: null,
        phone: null,
        nextContact: null,
        caseManager: null,
        caseExpert: null
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
      { text: "Assigned To", value: "contactName" },
      { text: "Phone", value: "phone" },
      { text: "Next Contact", value: "nextContact" },
      { text: "Case Manager", value: "caseManager" },
      { text: "Case Expert", value: "caseExpert" }
    ],
    clients: [
      {
        task: "Tagtune",
        contactName: "Wylie",
        phone: "959-950-8772",
        nextContact: "Bennie",
        caseManager: "Franzen",
        caseExpert: "Martino"
      },
      {
        task: "Wikizz",
        contactName: "Lilllie",
        phone: "135-373-4114",
        nextContact: "Clywd",
        caseManager: "Kristo",
        caseExpert: "Pierre"
      },
      {
        task: "Edgeblab",
        contactName: "Levin",
        phone: "804-861-8459",
        nextContact: "Lonny",
        caseManager: "Mordecai",
        caseExpert: "Lyle"
      },
      {
        task: "Flipbug",
        contactName: "Aldous",
        phone: "296-403-8485",
        nextContact: "Flossie",
        caseManager: "Inness",
        caseExpert: "Tann"
      },
      {
        task: "Tanoodle",
        contactName: "Son",
        phone: "314-940-8370",
        nextContact: "Romona",
        caseManager: "Torrin",
        caseExpert: "Torr"
      },
      {
        task: "Oyoloo",
        contactName: "Harbert",
        phone: "891-812-7371",
        nextContact: "Frants",
        caseManager: "Colan",
        caseExpert: "Dermot"
      },
      {
        task: "Tazzy",
        contactName: "Carol",
        phone: "602-215-8288",
        nextContact: "Nissie",
        caseManager: "Ettore",
        caseExpert: "Albie"
      }
    ]
  })
};
</script>

<style></style>
