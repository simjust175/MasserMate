<template>
  <div>
      <v-app-bar prominent :collapse="collapse" elevate="4" density="compact" scroll-behavior="elevate collapse" scroll-threshold="330">
          <!-- <v-app-bar-nav-icon></v-app-bar-nav-icon> -->

          <v-toolbar-title>
            <div class="d-flex">
            <v-img src="../../../public/logo/logo1.png" height="30" width="30" id="logo"></v-img>
          <div id="log-text" > GetRich</div></div></v-toolbar-title>

          <v-spacer></v-spacer>
          <v-btn icon="mdi-check" color="purple" @click="loggedIn = !loggedIn"></v-btn>
          <v-btn :icon="themeStateIcon" @click="toggleTheme" variant="plain"></v-btn>
          <v-btn icon v-if="loggedIn">
              <v-icon @click="logout">mdi-export</v-icon>
          </v-btn>
          <v-btn color="purple" variant="outlined" class="mx-4" @click.stop="router.push('/register')" v-else>Login</v-btn>
      </v-app-bar>
  </div>
</template>

<script setup>
</script>

<script setup>
import { ref, computed, watch, defineProps, onMounted } from 'vue'
import { useTheme } from 'vuetify'
import { useRouter } from 'vue-router';

const router = useRouter();
const theme = useTheme();

function toggleTheme() {
  theme.global.name.value = theme.global.current.value.dark ? 'light' : 'dark'
}

const themeStateIcon = computed(() => theme.global.current.value.dark ? 'mdi-weather-night' : 'mdi-white-balance-sunny')

const props = defineProps({
  loggedInStat: Boolean,
  logout: Boolean,
  user_email: String
});

const loggedIn = ref(props.loggedInStat);

watch(() => props.loggedInStat, (newVal) => {
  loggedIn.value = newVal;
});
watch(() => props.logout, () => {
  console.log("logout triggered");
  logout();
});

// const logout = async () => {
//   console.log("entered logout");
//   const res = await fetch(`http://localhost:3399/register/logout/${localStorage.getItem("user_email")}`, {
//       method: "POST",
//       headers: {
//           "Content-Type": "application/json"
//       }
//   });
//   const data = await res.json();
//   console.log("logout", data);
//   if (data.Success) {
//       localStorage.removeItem("token");
//       loggedIn.value = false;
//       router.push("/register")
//   }
// }

</script>

<style scoped>
#logo{
  z-index: 1;
}

#logo-text{
  z-index: 2;
}
</style>