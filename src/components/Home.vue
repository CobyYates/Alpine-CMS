<template>
  <v-container fluid class="fluid">
    <v-row>
      <!-- <v-col cols="1" class="mx-3">
        <p>Projects</p>
        <v-row v-for="project in projects" :key="project.i">
          <v-btn width="150" class="my-1">{{ project.name }}</v-btn>
        </v-row>
      </v-col> -->
      <v-col cols="1" class="mx-3">
        <p>Staff</p>
        <v-row v-for="staff in staffs" :key="staff.i">
          <v-btn width="150" class="my-1">{{ staff.name }}</v-btn>
        </v-row>
      </v-col>
      <v-col cols="7" class="mx-3">
        <p>Clients</p>
        <v-data-table
          items-per-page="25"
          dense
          :headers="headers"
          :items="clients"
          item-key="name"
          class="elevation-1"
        ></v-data-table>
      </v-col>
      <v-col cols="3" class="mx-3">
        <p>Tasks</p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",

  data: () => ({
    // projects: [
    //   { name: "Project 1" },
    //   { name: "Project 2" },
    //   { name: "Project 3" },
    //   { name: "Project 4" },
    //   { name: "Project 5" },
    //   { name: "Project 6" },
    //   { name: "Project 7" },
    //   { name: "Project 8" },
    //   { name: "Project 9" },
    //   { name: "Project 10" },
    //   { name: "Project 11" },
    //   { name: "Project 12" },
    //   { name: "Project 13" },
    //   { name: "Project 14" },
    //   { name: "Project 15" },
    //   { name: "Project 16" },
    //   { name: "Project 17" }
    // ],
    staffs: [
      { name: "Shawn" },
      { name: "Jane" },
      { name: "Ronald" },
      { name: "Joe" },
      { name: "Dylan" },
      { name: "Joshua" },
      { name: "Ralph" },
      { name: "Cory" },
      { name: "Jordan" },
      { name: "Jack" },
      { name: "Carl" }
    ],
    clients: [
      {
        name: "Frozen Yogurt",
        contactName: 159,
        phone: 6.0,
        nextContact: 24,
        caseManager: 4.0,
        caseExpert: "1%"
      },
      {
        name: "Ice cream sandwich",
        contactName: 237,
        phone: 9.0,
        nextContact: 37,
        caseManager: 4.3,
        caseExpert: "1%"
      },
      {
        name: "Eclair",
        contactName: 262,
        phone: 16.0,
        nextContact: 23,
        caseManager: 6.0,
        caseExpert: "7%"
      },
      {
        name: "Cupcake",
        contactName: 305,
        phone: 3.7,
        nextContact: 67,
        caseManager: 4.3,
        caseExpert: "8%"
      },
      {
        name: "Gingerbread",
        contactName: 356,
        phone: 16.0,
        nextContact: 49,
        caseManager: 3.9,
        caseExpert: "16%"
      },
      {
        name: "Jelly bean",
        contactName: 375,
        phone: 0.0,
        nextContact: 94,
        caseManager: 0.0,
        caseExpert: "0%"
      },
      {
        name: "Lollipop",
        contactName: 392,
        phone: 0.2,
        nextContact: 98,
        caseManager: 0,
        caseExpert: "2%"
      },
      {
        name: "Honeycomb",
        contactName: 408,
        phone: 3.2,
        nextContact: 87,
        caseManager: 6.5,
        caseExpert: "45%"
      },
      {
        name: "Donut",
        contactName: 452,
        phone: 25.0,
        nextContact: 51,
        caseManager: 4.9,
        caseExpert: "22%"
      },
      {
        name: "KitKat",
        contactName: 518,
        phone: 26.0,
        nextContact: 65,
        caseManager: 7,
        caseExpert: "6%"
      },
      {
        name: "Frozen Yogurt",
        contactName: 159,
        phone: 6.0,
        nextContact: 24,
        caseManager: 4.0,
        caseExpert: "1%"
      },
      {
        name: "Ice cream sandwich",
        contactName: 237,
        phone: 9.0,
        nextContact: 37,
        caseManager: 4.3,
        caseExpert: "1%"
      },
      {
        name: "Eclair",
        contactName: 262,
        phone: 16.0,
        nextContact: 23,
        caseManager: 6.0,
        caseExpert: "7%"
      },
      {
        name: "Cupcake",
        contactName: 305,
        phone: 3.7,
        nextContact: 67,
        caseManager: 4.3,
        caseExpert: "8%"
      },
      {
        name: "Gingerbread",
        contactName: 356,
        phone: 16.0,
        nextContact: 49,
        caseManager: 3.9,
        caseExpert: "16%"
      },
      {
        name: "Jelly bean",
        contactName: 375,
        phone: 0.0,
        nextContact: 94,
        caseManager: 0.0,
        caseExpert: "0%"
      },
      {
        name: "Lollipop",
        contactName: 392,
        phone: 0.2,
        nextContact: 98,
        caseManager: 0,
        caseExpert: "2%"
      },
      {
        name: "Honeycomb",
        contactName: 408,
        phone: 3.2,
        nextContact: 87,
        caseManager: 6.5,
        caseExpert: "45%"
      },
      {
        name: "Donut",
        contactName: 452,
        phone: 25.0,
        nextContact: 51,
        caseManager: 4.9,
        caseExpert: "22%"
      },
      {
        name: "KitKat",
        contactName: 518,
        phone: 26.0,
        nextContact: 65,
        caseManager: 7,
        caseExpert: "6%"
      }
    ],
    headers: [
      {
        text: "Case Name",
        align: "start",
        sortable: false,
        value: "name"
      },
      { text: "Contact Name", value: "contactName" },
      { text: "Phone", value: "phone" },
      { text: "Next Contact", value: "nextContact" },
      { text: "Case Manager", value: "caseManager" },
      { text: "Case Expert", value: "caseExpert" }
    ]
  })
};
</script>
