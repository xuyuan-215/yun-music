<template>
  <div>
    <v-row>
      <v-col v-for="(item, i) in items" :key="i" cols="6">
        <v-card :color="item.color" dark>
          <div class="d-flex flex-no-wrap justify-space-between">
            <div>
              <v-card-title class="headline" v-text="item.title"></v-card-title>

              <v-card-subtitle v-text="item.artist"></v-card-subtitle>
            </div>

            <v-avatar class="ma-3" size="125" tile>
              <v-img :src="item.src"></v-img>
            </v-avatar>
          </div>
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-card class="mx-auto" max-width="344">
        <v-img src="https://p3fx.kgimg.com/stdmusic/20150720/20150720202728298178.jpg" height="200px"></v-img>

        <v-card-title>
          Top western road trips
        </v-card-title>

        <v-card-subtitle>
          1,000 miles of wonder
        </v-card-subtitle>

        <v-card-actions>
          <v-btn text>Share</v-btn>

          <v-btn color="purple" text>
            Explore
          </v-btn>

          <v-spacer></v-spacer>

          <v-btn icon @click="show = !show">
            <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
          </v-btn>
        </v-card-actions>

        <v-expand-transition>
          <div v-show="show">
            <v-divider></v-divider>

            <v-card-text>
              I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier,
              not with all the bed making you'll be doing.
            </v-card-text>
          </div>
        </v-expand-transition>
      </v-card>
      <v-card class="mx-auto" max-width="344">
        <v-img src="https://p3fx.kgimg.com/stdmusic/20160623/20160623001308858934.jpg" height="200px"></v-img>

        <v-card-title>
          Top western road trips
        </v-card-title>

        <v-card-subtitle>
          1,000 miles of wonder
        </v-card-subtitle>

        <v-card-actions>
          <v-btn text>Share</v-btn>

          <v-btn color="purple" text>
            Explore
          </v-btn>

          <v-spacer></v-spacer>

          <v-btn icon @click="show = !show">
            <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
          </v-btn>
        </v-card-actions>

        <v-expand-transition>
          <div v-show="show">
            <v-divider></v-divider>

            <v-card-text>
              I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier,
              not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we
              walk! You're going to do his laundry? I've got to find a way to escape.
            </v-card-text>
          </div>
        </v-expand-transition>
      </v-card>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'Dashboard',
  data: () => ({
    show: false,
    items: [
      {
        color: '#1F7087',
        src: 'https://cdn.vuetifyjs.com/images/cards/foster.jpg',
        title: 'Supermodel',
        artist: 'Foster the People'
      },
      {
        color: '#952175',
        src: 'https://cdn.vuetifyjs.com/images/cards/halcyon.png',
        title: 'Halcyon Days',
        artist: 'Ellie Goulding'
      }
    ]
  })
}
</script>

<style scoped lang="scss"></style>
