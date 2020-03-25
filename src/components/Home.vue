<template>
  <v-container fluid class="fluid">
    <v-row class="text-center">
      <!-- <v-col cols="1" class="mx-3">
        <p>Projects</p>
        <v-row v-for="project in projects" :key="project.i">
          <v-btn width="150" class="my-1">{{ project.name }}</v-btn>
        </v-row>
      </v-col> -->
      <v-col cols="1" class="px-3">
        <p class="display-1">Staff</p>
        <v-row v-for="staff in staffs" :key="staff.i">
          <v-btn color="success" width="100%" class="my-1">{{
            staff.name
          }}</v-btn>
        </v-row>
      </v-col>
      <v-col cols="7" class="px-3">
        <p class="display-1">Clients</p>
        <v-data-table
          items-per-page="25"
          dense
          :headers="headers"
          :items="clients"
          item-key="name"
          class="elevation-1"
        ></v-data-table>
      </v-col>
      <v-col cols="4" class="px-3">
        <p class="display-1">Tasks</p>
        <v-data-table
          items-per-page="25"
          dense
          :headers="headers"
          :items="clients"
          item-key="name"
          class="elevation-1"
        ></v-data-table>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",

  data: () => ({
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
        caseName: "Tagtune",
        contactName: "Wylie",
        phone: "959-950-8772",
        nextContact: "Bennie",
        caseManager: "Franzen",
        caseExpert: "Martino"
      },
      {
        caseName: "Wikizz",
        contactName: "Lilllie",
        phone: "135-373-4114",
        nextContact: "Clywd",
        caseManager: "Kristo",
        caseExpert: "Pierre"
      },
      {
        caseName: "Edgeblab",
        contactName: "Levin",
        phone: "804-861-8459",
        nextContact: "Lonny",
        caseManager: "Mordecai",
        caseExpert: "Lyle"
      },
      {
        caseName: "Flipbug",
        contactName: "Aldous",
        phone: "296-403-8485",
        nextContact: "Flossie",
        caseManager: "Inness",
        caseExpert: "Tann"
      },
      {
        caseName: "Tanoodle",
        contactName: "Son",
        phone: "314-940-8370",
        nextContact: "Romona",
        caseManager: "Torrin",
        caseExpert: "Torr"
      },
      {
        caseName: "Oyoloo",
        contactName: "Harbert",
        phone: "891-812-7371",
        nextContact: "Frants",
        caseManager: "Colan",
        caseExpert: "Dermot"
      },
      {
        caseName: "Tazzy",
        contactName: "Carol",
        phone: "602-215-8288",
        nextContact: "Nissie",
        caseManager: "Ettore",
        caseExpert: "Albie"
      },
      {
        caseName: "Flipbug",
        contactName: "Rosaline",
        phone: "247-647-4904",
        nextContact: "Nadia",
        caseManager: "Bryanty",
        caseExpert: "Sutherlan"
      },
      {
        caseName: "Topdrive",
        contactName: "Nicola",
        phone: "536-554-8146",
        nextContact: "Shep",
        caseManager: "Corty",
        caseExpert: "Christy"
      },
      {
        caseName: "Npath",
        contactName: "Gottfried",
        phone: "344-131-2568",
        nextContact: "Brynn",
        caseManager: "Ganny",
        caseExpert: "Dew"
      },
      {
        caseName: "Oba",
        contactName: "Bobina",
        phone: "517-352-7198",
        nextContact: "Charla",
        caseManager: "Sampson",
        caseExpert: "Kermie"
      },
      {
        caseName: "Yambee",
        contactName: "Giustino",
        phone: "276-533-0963",
        nextContact: "Joyous",
        caseManager: "Frasier",
        caseExpert: "Fonzie"
      },
      {
        caseName: "Reallinks",
        contactName: "Gregor",
        phone: "305-322-7630",
        nextContact: "Ara",
        caseManager: "Waylen",
        caseExpert: "Umberto"
      },
      {
        caseName: "Blogtags",
        contactName: "Estella",
        phone: "860-278-6527",
        nextContact: "Lula",
        caseManager: "Roth",
        caseExpert: "Tris"
      },
      {
        caseName: "Meedoo",
        contactName: "Barbabas",
        phone: "463-576-7559",
        nextContact: "Crichton",
        caseManager: "Irvine",
        caseExpert: "Tarrance"
      },
      {
        caseName: "Flashset",
        contactName: "Desdemona",
        phone: "731-808-4081",
        nextContact: "Andrei",
        caseManager: "Kirk",
        caseExpert: "Harris"
      },
      {
        caseName: "Innojam",
        contactName: "Tessi",
        phone: "769-278-0140",
        nextContact: "Serene",
        caseManager: "Felic",
        caseExpert: "Shelton"
      },
      {
        caseName: "Jabbercube",
        contactName: "Eward",
        phone: "126-618-1009",
        nextContact: "Janka",
        caseManager: "Thedrick",
        caseExpert: "Cornall"
      },
      {
        caseName: "Jaxnation",
        contactName: "Paxton",
        phone: "432-203-1866",
        nextContact: "Rockey",
        caseManager: "August",
        caseExpert: "Garv"
      },
      {
        caseName: "Shufflester",
        contactName: "Alie",
        phone: "199-853-9485",
        nextContact: "Issi",
        caseManager: "Urbano",
        caseExpert: "Perren"
      },
      {
        caseName: "Buzzdog",
        contactName: "Ivor",
        phone: "504-773-0367",
        nextContact: "Meggie",
        caseManager: "Krishnah",
        caseExpert: "Isiahi"
      },
      {
        caseName: "Kaymbo",
        contactName: "Cthrine",
        phone: "678-429-0874",
        nextContact: "Jeanie",
        caseManager: "Delmar",
        caseExpert: "Mickey"
      },
      {
        caseName: "Youtags",
        contactName: "Wilhelm",
        phone: "460-880-8656",
        nextContact: "Findlay",
        caseManager: "Urban",
        caseExpert: "Cletis"
      },
      {
        caseName: "Edgewire",
        contactName: "Danyette",
        phone: "893-782-6707",
        nextContact: "Mag",
        caseManager: "Morgun",
        caseExpert: "Jarrad"
      },
      {
        caseName: "Camido",
        contactName: "Quinta",
        phone: "970-181-3906",
        nextContact: "Alphard",
        caseManager: "Frederic",
        caseExpert: "Jerry"
      },
      {
        caseName: "Yozio",
        contactName: "Zabrina",
        phone: "828-330-9861",
        nextContact: "Sibilla",
        caseManager: "Dougy",
        caseExpert: "Barnie"
      },
      {
        caseName: "Avamba",
        contactName: "Cher",
        phone: "538-300-8213",
        nextContact: "Ermin",
        caseManager: "Kayne",
        caseExpert: "Julio"
      },
      {
        caseName: "Kazio",
        contactName: "Buiron",
        phone: "818-360-0447",
        nextContact: "Timmy",
        caseManager: "Blake",
        caseExpert: "Yard"
      },
      {
        caseName: "Edgeblab",
        contactName: "Derby",
        phone: "419-343-0513",
        nextContact: "Dasya",
        caseManager: "Rusty",
        caseExpert: "Grange"
      },
      {
        caseName: "Wordify",
        contactName: "Ediva",
        phone: "235-690-5746",
        nextContact: "Dore",
        caseManager: "Lowe",
        caseExpert: "Carling"
      },
      {
        caseName: "Abatz",
        contactName: "Tiena",
        phone: "382-978-0677",
        nextContact: "Granger",
        caseManager: "Monroe",
        caseExpert: "Raimondo"
      },
      {
        caseName: "Edgewire",
        contactName: "Jewel",
        phone: "531-462-5839",
        nextContact: "Corbett",
        caseManager: "Jefferey",
        caseExpert: "Kermie"
      },
      {
        caseName: "Realcube",
        contactName: "Myra",
        phone: "415-804-0788",
        nextContact: "Andie",
        caseManager: "Henri",
        caseExpert: "Max"
      },
      {
        caseName: "Leenti",
        contactName: "Barbe",
        phone: "935-825-2147",
        nextContact: "Mariejeanne",
        caseManager: "Graehme",
        caseExpert: "Kendricks"
      },
      {
        caseName: "Centidel",
        contactName: "Daria",
        phone: "739-919-8290",
        nextContact: "Wini",
        caseManager: "Ward",
        caseExpert: "Lief"
      },
      {
        caseName: "Aimbu",
        contactName: "Crawford",
        phone: "608-635-1279",
        nextContact: "Marlena",
        caseManager: "Shalom",
        caseExpert: "Garek"
      },
      {
        caseName: "Feedmix",
        contactName: "Klarrisa",
        phone: "808-601-9646",
        nextContact: "Eachelle",
        caseManager: "Em",
        caseExpert: "Hastings"
      },
      {
        caseName: "Zoomcast",
        contactName: "Jelene",
        phone: "631-686-1107",
        nextContact: "Casie",
        caseManager: "Alfie",
        caseExpert: "Ansell"
      },
      {
        caseName: "Yodo",
        contactName: "Shana",
        phone: "989-621-8280",
        nextContact: "Seline",
        caseManager: "Allister",
        caseExpert: "Cassius"
      },
      {
        caseName: "Skippad",
        contactName: "Liza",
        phone: "791-245-2067",
        nextContact: "Cyrus",
        caseManager: "Ulick",
        caseExpert: "Terrel"
      }
    ],
    headers: [
      {
        text: "Case Name",
        align: "start",
        sortable: false,
        value: "caseName"
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
