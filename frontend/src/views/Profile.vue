<template>
  <div>
    <Navbar :page="'profile'" />
    <div class="page-container">
      <Topbar />
      <div class="profile-page">
        <div class="profile-page-container">
          <div class="profile-heading">My profile</div>
          <div class="profile">
            <div class="user-name">{{ $store.getters.getUser.name }}</div>
            <div class="user-email">{{ $store.getters.getUser.email }}</div>
            <div class="issue-status">
              <div class="issue-field">
                <div class="issue-title">Total</div>
                <div class="issue-count">
                  {{ $store.getters.getTaskCount.total }}
                </div>
              </div>
              <div class="issue-field">
                <div class="issue-title">Todo</div>
                <div class="issue-count">
                  {{ $store.getters.getTaskCount.todo }}
                </div>
              </div>
              <div class="issue-field">
                <div class="issue-title">Doing</div>
                <div class="issue-count">
                  {{ $store.getters.getTaskCount.doing }}
                </div>
              </div>
              <div class="issue-field">
                <div class="issue-title">Done</div>
                <div class="issue-count">
                  {{ $store.getters.getTaskCount.total }}
                </div>
              </div>
              <div class="cta">
                <router-link class="home-navigation" to="/">
                  Go back to home
                </router-link>
                <span class="logout" @click="logout"> Logout </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue';
import Topbar from '@/components/Topbar.vue';

export default {
  name: 'Profile',
  components: {
    Navbar,
    Topbar,
  },
  methods: {
    logout() {
      this.$store.dispatch('logout');
      this.$store.dispatch('loadUserInfo');
    },
  },
};
</script>
<style lang="scss" scoped>
@import '../styles/profile.page.styles.scss';
</style>
