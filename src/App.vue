<template>
    <v-app>
        <v-app-bar
            app
            color="grey lighten-3"
            dark
        >
            <v-btn icon color="black" @click="$router.push('/')">
                <v-icon>mdi-home</v-icon>
            </v-btn>
            <v-spacer></v-spacer>
            <v-menu
                top
                :close-on-click="closeOnClick"
                >
                <template v-slot:activator="{ on, attrs }">
                    <v-btn icon color="black" v-bind="attrs" v-on="on">
                        <v-icon>mdi-dots-vertical</v-icon>
                    </v-btn>
                </template>

                <v-list>
                    <v-list-item
                    v-for="(item, index) in items"
                    :key="index"
                    :to="item.to"
                    >
                    <v-list-item-title>{{ item.title }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>
        </v-app-bar>
        <v-main>
            <router-view></router-view>
        </v-main>
    </v-app>
</template>

<script>

export default {
  name: 'App',

  components: {
  },

  data: () => ({
    items: [
        { title: 'Ocr Upload', to: '/ocr-upload'},
        { title: 'Title 1', to: '/'},
        { title: 'Title 2', to: '/'},
      ],
      closeOnClick: true,
  }),
};
</script>
