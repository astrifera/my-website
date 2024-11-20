<script setup>
import {onMounted, ref} from 'vue';
import logo from './assets/logo_ho-01-optimized.svg';
import insta from './assets/1f_insta.svg';
import dribbble from './assets/2f_dribbble.svg';
import lkin from './assets/3f_lkin.svg';
import mail from './assets/4f_mail.svg';
import gsap from 'gsap';

const modal = ref(null)

const links = {
  tree: [
    // {
    //   href: null,
    //   dialog: true,
    //   label: 'About and blah blah blah',
    //   color: 'var(--h-brown)',
    //   background: 'var(--h-yellow)',
    // },
    {
      href: 'https://dribbble.com/hosannagambus',
      label: 'My portafolio',
      color: 'var(--h-brown)',
      background: 'var(--h-pink)',
    },
    {
      href: 'https://www.etsy.com/ca/shop/HosannaDesignShop?ref=l2-about-shopname',
      label: 'Etsy shop',
      color: 'var(--h-background)',
      background: 'var(--h-pink2)',
    },
    {
      href: 'https://society6.com/astrifera',
      label: 'Society6 store',
      color: 'var(--h-brown)',
      background: 'var(--h-orange)',
    },

  ],
  footer: [
    {
      href: 'https://www.instagram.com/hosannagambus/',
      image: insta,
    },
    {
      href: 'https://dribbble.com/hosannagambus/about',
      image: dribbble,
    },
    {
      href: 'https://www.linkedin.com/in/hosanna-gamb%C3%BAs-28161846/',
      image: lkin,
    },
    {
      href: 'mailto:astrifera@gmail.com',
      image: mail,
    }
  ],
}

function openDialog() {
  modal.value.showModal();
}

function closeDialog() {
  modal.value.close();
}

onMounted(() => {
  gsap.from(".logo", {y: -20, opacity: 0, duration: 0.6, stagger: 0.1});
  gsap.from(".link-tree-list-item", {y: -20, opacity: 0, duration: 0.6, stagger: 0.1, delay: 0.2});
  gsap.from(".social-media-list-item", {y: -20, opacity: 0, duration: 0.6, stagger: 0.1, delay: 0.4});
});
</script>

<template>
  <header>
      <img class="logo" :src="logo" alt="">
  </header>
  <section class="link-tree">
      <ul class="link-tree-list">
          <li class="link-tree-list-item" v-for="(link, index) in links.tree" :key="index">
              <a v-if="link.href" :style="{color: link.color, background: link.background}" :href="link.href" target="_blank">{{ link.label }}</a>
              <a v-else :style="{color: link.color, background: link.background}" @click="openDialog">{{ link.label }}</a>
          </li>
      </ul>
  </section>
  <!-- <dialog ref="modal">
    <div class="close-about-me" @click="closeDialog"></div>
  </dialog> -->
  <footer>
      <ul class="social-media-list">
        <li class="social-media-list-item" v-for="(footerLink, index) in links.footer" :key="index">
          <a :href="footerLink.href" target="_blank">
            <img :src="footerLink.image" alt="">
          </a>
        </li>
      </ul>
  </footer>
</template>
