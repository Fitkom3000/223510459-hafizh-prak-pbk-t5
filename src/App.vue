<template>
  <div class="q-pa-md">
    <q-layout view="lHh lpr lFf" container class="shadow-2 rounded-borders fullscreen">
      <q-header reveal elevated>
        <q-toolbar>
          <q-btn flat round dense icon="menu" @click="drawer = !drawer" class="q-mr-sm" />
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          <q-toolbar-title>Kue Lebaran Balfizh</q-toolbar-title>
          <q-btn flat round dense icon="whatshot" />
        </q-toolbar>
      </q-header>

      <q-drawer
        v-model="drawer"
        side="left"
        show-if-above
        :width="200"
        bordered
        :class="$q.dark.isActive ? 'bg-grey-9' : 'bg-grey-3'"
      >
        <q-scroll-area class="fit">
          <q-list>
            <template v-for="(menuItem, index) in menuList" :key="index">
              <q-item clickable :active="menuItem.label === 'Outbox'" v-ripple>
                <q-item-section avatar>
                  <q-icon :name="menuItem.icon" />
                </q-item-section>
                <q-item-section>
                  {{ menuItem.label }}
                </q-item-section>
              </q-item>
              <q-separator :key="'sep' + index" v-if="menuItem.separator" />
            </template>
          </q-list>
        </q-scroll-area>
      </q-drawer>

      <q-page-container>
        <q-page class="q-pa-md fit">
          <div class="q-pa-md">
            <q-carousel animated v-model="slide" arrows navigation infinite>
              <q-carousel-slide :name="1" img-src="/assets/nastar.jpg" />
              <q-carousel-slide :name="2" img-src="/assets/nastarKurma.jpg" />
              <q-carousel-slide :name="3" img-src="/assets/chocoChipCookies.jpg" />
              <q-carousel-slide :name="4" img-src="/assets/pastelKering.jpg" />
              <q-carousel-slide :name="5" img-src="/assets/butterCookie.jpg" />
              <q-carousel-slide :name="6" img-src="/assets/kembangGoyang.jpg" />
              <q-carousel-slide :name="7" img-src="/assets/kueKacangTanah.jpg" />
              <q-carousel-slide :name="8" img-src="/assets/lidahKucing.jpg" />
              <q-carousel-slide :name="9" img-src="/assets/keciput.jpg" />
              <q-carousel-slide :name="10" img-src="/assets/kastengel.jpg" />
            </q-carousel>
          </div>
        </q-page>

        <q-page padding>
          <div class="q-pa-md column items-start q-gutter-md">
            <q-card v-for="(card, index) in cards" :key="index" class="my-card" flat bordered>
              <q-img :src="card.img" />

              <q-card-section>
                <div class="text-overline text-orange-9">{{ card.overline }}</div>
                <div class="text-h5 q-mt-sm q-mb-xs">{{ card.title }}</div>
                <div class="text-caption text-grey">
                  {{ card.description }}
                </div>
              </q-card-section>

              <q-card-actions>
                <q-btn flat color="primary" label="Beli Langsung" />
                <q-btn flat color="secondary" label="Masuk Keranjang" />

                <q-space />

                <q-btn
                  color="grey"
                  round
                  flat
                  dense
                  :icon="card.expanded ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"
                  @click="card.expanded = !card.expanded"
                />
              </q-card-actions>

              <q-slide-transition>
                <div v-show="card.expanded">
                  <q-separator />
                  <q-card-section class="text-subtitle2">
                    {{ card.lorem }}
                  </q-card-section>
                </div>
              </q-slide-transition>
            </q-card>
          </div>
        </q-page>
      </q-page-container>

      <q-footer reveal elevated>
        <q-toolbar>
          <q-toolbar-title>Tugas 5 Praktikum Pemrograman Berbasis Komponen</q-toolbar-title>
        </q-toolbar>
      </q-footer>
    </q-layout>
  </div>
</template>

<script>
import { ref } from 'vue'

const menuList = [
  {
    icon: 'shopping_cart',
    label: 'Keranjang',
    separator: false
  },
  {
    icon: 'favorite',
    label: 'Disukai',
    separator: true
  },
  {
    icon: 'settings',
    label: 'Pengaturan',
    separator: false
  },
  {
    icon: 'feedback',
    label: 'Kirim Masukan',
    separator: false
  },
  {
    icon: 'help',
    iconColor: 'primary',
    label: 'Bantuan',
    separator: false
  }
]

export default {
  setup() {
    const cards = ref([
      {
        img: '/assets/nastar.jpg',
        overline: 'Kue Kering',
        title: 'Nastar',
        expanded: false,
        lorem: 'Nastar adalah perwujudan dari perpaduan rasa manis yang melambangkan keindahan hidup, yang diimbangi dengan kegurihan adonan yang mengingatkan kita akan kompleksitas dalam mencapai kesempurnaan.'
      },
      {
        img: '/assets/nastarKurma.jpg',
        overline: 'Kue Kering',
        title: 'Nastar Kurma',
        expanded: false,
        lorem: 'Nastar Kurma adalah kue yang menggabungkan rasa manis dari kurma dengan tekstur renyah khas nastar. Kue ini menggambarkan perpaduan unik antara kelembutan kurma dan kegurihan adonan kue yang membuatnya menjadi pilihan yang menggugah selera untuk dinikmati dalam suasana santai atau momen spesial.'
      },
      {
        img: '/assets/chocoChipCookies.jpg',
        overline: 'Kue Kering',
        title: 'Choco Chip Cookies',
        expanded: false,
        lorem: 'Choco Chip Cookies adalah kue kering yang terkenal dengan campuran lezat antara cokelat dan adonan kue yang renyah. Kue ini menghadirkan kesempurnaan rasa manis dari cokelat yang meleleh di mulut, sekaligus kegurihan dari adonan yang memberikan sensasi menggigit yang memuaskan.'
      },
      {
        img: '/assets/pastelKering.jpg',
        overline: 'Kue Kering',
        title: 'Pastel Kering',
        expanded: false,
        lorem: 'Pastel kering adalah kue kering yang lembut dengan rasa manis yang diimbangi dengan tekstur renyahnya. Kue ini menciptakan harmoni unik antara kelembutan dan kegurihan, memberikan pengalaman mengunyah yang memuaskan dengan setiap gigitannya.'
      },
      {
        img: '/assets/butterCookie.jpg',
        overline: 'Kue Kering',
        title: 'Butter Cookie',
        expanded: false,
        lorem: 'Butter Cookies adalah kue kering yang terkenal dengan cita rasa lembut dan kaya mentega. Kue ini menggambarkan kesederhanaan yang elegan, di mana kelezatan dari mentega bersatu dalam harmoni dengan kegurihan adonan yang renyah. Butter Cookies menghadirkan pengalaman menyantap yang memanjakan lidah dengan rasa yang lembut namun kaya akan cita rasa mentega.'
      },
      {
        img: '/assets/kembangGoyang.jpg',
        overline: 'Kue Kering',
        title: 'Kembang Goyang',
        expanded: false,
        lorem: 'Kembang Goyang adalah salah satu jenis kue tradisional Indonesia yang terkenal dengan bentuknya yang unik menyerupai kembang yang sedang mekar. Kue ini terbuat dari adonan yang digoreng hingga renyah dan sering disajikan sebagai cemilan atau hidangan ringan. Rasanya yang gurih dan teksturnya yang renyah membuatnya menjadi favorit di berbagai acara atau sebagai camilan sehari-hari.'
      },
      {
        img: '/assets/kueKacangTanah.jpg',
        overline: 'Kue Kering',
        title: 'Kue Kacang Tanah',
        expanded: false,
        lorem: 'Kue Kacang Tanah adalah kue tradisional yang terbuat dari campuran kacang tanah yang dihaluskan, gula, dan tepung terigu. Kue ini memiliki tekstur yang renyah namun lembut di dalamnya. Rasanya manis dengan aroma khas kacang tanah yang sangat menggugah selera. Kue Kacang Tanah sering disajikan sebagai camilan di berbagai acara atau sebagai hidangan ringan sehari-hari.'
      },
      {
        img: '/assets/lidahKucing.jpg',
        overline: 'Kue Kering',
        title: 'Lidah Kucing',
        expanded: false,
        lorem: 'Lidah Kucing adalah kue kering yang terkenal dengan bentuknya yang tipis dan panjang, menyerupai lidah kucing. Kue ini terbuat dari adonan yang terdiri dari mentega, gula, tepung terigu, dan telur yang kemudian dipanggang hingga menjadi renyah. Lidah Kucing memiliki rasa yang ringan, manis, dan gurih, membuatnya menjadi camilan yang populer di berbagai kesempatan, mulai dari acara formal hingga santai.'
      },
      {
        img: '/assets/keciput.jpg',
        overline: 'Kue Kering',
        title: 'Keciput',
        expanded: false,
        lorem: 'Keciput adalah kue tradisional Indonesia yang terbuat dari campuran tepung terigu, air, garam, dan minyak. Adonan keciput kemudian digoreng hingga mengembang dan menjadi renyah. Kue ini memiliki tekstur yang ringan dan berpori-pori, serta rasanya yang gurih dengan sedikit rasa manis. Keciput sering disajikan sebagai camilan atau hidangan ringan yang disukai banyak orang karena teksturnya yang unik dan cita rasanya yang lezat.'
      },
      {
        img: '/assets/kastengel.jpg',
        overline: 'Kue Kering',
        title: 'Kastengel',
        expanded: false,
        lorem: 'Kue kastengel adalah simbol perpaduan budaya dan kekuatan komunitas dalam proses pembuatannya.'
      }
    ]);

    return {
      slide: ref(1),
      drawer: ref(false),
      menuList,
      cards
    }
  }
}
</script>

<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 350px
</style>
