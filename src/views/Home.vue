<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <p>
      <button
        class="button"
        v-if="notificationsSupported"
        v-on:click="askPermission()"
      >Enable notifications</button>
    </p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Component from 'vue-class-component';

@Component({})
export default class Home extends Vue {

  notificationsSupported = false;

  constructor() {
    super();
  }

  mounted() { }

  askPermission() {
    console.log('Button clicked');
    if (this.notificationsSupported) {
      Notification.requestPermission(result => {
        console.log('result from permission question', result);
        if (result !== 'granted') {
          alert('You probably do not like notifications?!');
        } else {
          console.log('A notification will be send from the service worker => This only works in production');
          this.showNotification();
        }
      });
    }
  }

  showNotification() {
    if ('serviceWorker' in navigator) {
      navigator.serviceWorker.ready // returns a Promise, the active SW registration
        .then(swreg => swreg.showNotification('Notifications granted', {
          body: 'Here is a first notification',
          icon: '/img/icons/android-chrome-192x192.png',
          // image: '/img/autumn-forest.png',
          // vibrate: [300, 200, 300],
          // badge: '/img/icons/plint-badge-96x96.png',
          // actions: [
          //     { action: 'confirm', title: 'Okay', icon: '/img/icons/android-chrome-192x192.png'},
          //     { action: 'cancel', title: 'Cancel', icon: '/img/icons/android-chrome-192x192.png'}
          // ],
        }));
    }
  }

  created() {
    if ('Notification' in window && 'serviceWorker' in navigator) {
      this.notificationsSupported = true;
    }
  }
}
</script>

<style lang="scss" scoped>
.button {
  height: 40px;
  background: #42b983;
  font-size: 16px;
  color: #fff;
  border: 0;
  outline: none;
  box-shadow: 2px 2px 2px #eee;
  cursor: pointer;
  border-radius: 2px;

  &:active {
    box-shadow: 2px 2px 2px #bbb;
  }
}
</style>

