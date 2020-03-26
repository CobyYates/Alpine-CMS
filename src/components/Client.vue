<template>
  <v-row>
    <v-col cols="4">
      <v-row v-for="detail in caseDetails" :key="detail.i" class="my-0 py-0">
        <v-col cols="4" class="px-0">
          <p>{{ detail.name }}</p>
        </v-col>
        <v-text-field
          v-if="!detail.select"
          outlined
          class="my-0 py-0"
        ></v-text-field>
        <v-select
          v-if="detail.select"
          :items="detail.selects"
          label="Solo field"
          solo
        ></v-select>
      </v-row>
    </v-col>
    <v-col cols="5">
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

        <v-tab v-for="i in tabs" :key="i" :href="`#tab-${i}`">
          {{ i }}
        </v-tab>

        <v-tab-item v-for="test in tabs" :key="test" :value="'tab-' + test">
          <v-card flat tile>
            <!-- <div v-if="i === 'Contact Information'"> -->
              <v-row v-for="item in tabForm[0]" :key="item" class="mx-3">
                <v-col cols="3">
                  <p>{{ item.name }}</p>
                </v-col>
                <v-col cols="9">
                  <v-text-field outlined v-if="item.input"></v-text-field>
                  <v-select v-if="item.select" outlined :items="item.items"></v-select>
                  <v-textarea v-if="item.area" outlined></v-textarea>
                </v-col>
                
              </v-row>
            <!-- </div> -->
          </v-card>
        </v-tab-item>
      </v-tabs>
    </v-col>
    <v-col></v-col>
  </v-row>
</template>

<script>
export default {
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
    tabForm: [
      [
        { name: "Contact Name", input: true, select: false, area: false, icons: false },
        { name: "Company", input: false, select: true, area: false, icons: false, items: ["Company A", "Company B", "Company C"] },
        { name: "Email", input: true, select: false, area: false, icons: false },
        { name: "Phone", input: true, select: false, area: false, icons: false },
        { name: "Cell", input: true, select: false, area: false, icons: false },
        { name: "Comments", input: false, select: false, area: true, icons: false }
      ],
      [
        { name: "Contact Name", input: true, select: false, area: false, icons: false },
        { name: "Company", input: false, select: true, area: false, icons: false },
        { name: "Email", input: true, select: false, area: false, icons: false },
        { name: "Phone", input: true, select: false, area: false, icons: false },
        { name: "Cell", input: true, select: false, area: false, icons: false },
        { name: "Comments", input: false, select: false, area: true, icons: false }
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
    ]
  })
};
</script>

<style></style>
