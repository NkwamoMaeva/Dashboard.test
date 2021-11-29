<template>
  <div>
    <v-app-bar dense height="60px" color="white" elevation="0" app>
      <v-row no-gutters>
        <v-col>
          <v-app-bar-nav-icon color="primary"></v-app-bar-nav-icon>
        </v-col>
        <v-col class="d-flex justify-center align-center">
          <span class="text-subtitle-2">Dashboard</span>
        </v-col>
        <v-col class="d-flex justify-end">
          <div>
            <v-btn icon color="grey">
              <v-icon>mdi-magnify</v-icon>
            </v-btn>
            <v-btn icon color="grey">
              <v-badge content="2" color="error" overlap>
                <v-icon>mdi-bell-outline</v-icon>
              </v-badge>
            </v-btn>
            <v-avatar size="30px" class="ml-4">
              <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John" />
            </v-avatar>
          </div>
        </v-col>
      </v-row>
    </v-app-bar>
  </div>
</template>

<style lang="scss" scoped>
.w-100 {
  width: 100%;
}
</style>
