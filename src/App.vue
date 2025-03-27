<script setup>
import {onMounted, ref} from 'vue';
import logo from './assets/logo_ho-01-optimized.svg';
import insta from './assets/1f_insta.svg';
import dribbble from './assets/2f_dribbble.svg';
import lkin from './assets/3f_lkin.svg';
import mail from './assets/4f_mail.svg';
import gsap from 'gsap';

const modal = ref(null);

const linkedInUrl = "https://www.linkedin.com/in/hosanna-gamb%C3%BAs-28161846/";
const dribbbleUrl = "https://dribbble.com/hosannagambus";

const links = {
  tree: [
    {
      href: null,
      dialog: true,
      label: 'About and blah blah blah',
      color: 'var(--h-brown)',
      background: 'var(--h-yellow)',
    },
    {
      href: dribbbleUrl,
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
    // {
    //   href: 'https://society6.com/astrifera',
    //   label: 'Society6 store',
    //   color: 'var(--h-brown)',
    //   background: 'var(--h-orange)',
    // },

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
      href: linkedInUrl,
      image: lkin,
    },
    {
      href: 'mailto:astrifera@gmail.com',
      image: mail,
    }
  ],
};

function openDialog() {
  modal.value.showModal();
  modal.value.scrollTo(0, 0);
  gsap.from(".dialog-profile", {y: -20, opacity: 0, duration: 0.5, delay: 0.4});
  gsap.from(".dialog-content-copy article", {y: -20, opacity: 0, duration: 0.5, delay: 0.6});
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
  <dialog ref="modal">
    <div class="close-about-me" @click="closeDialog">
      <div class="close-about-me-icon"></div>
    </div>
    <div class="dialog-content">
      <div class="dialog-profile"></div>
      <div class="dialog-content-copy">
        <article>
          <h2>Hello.</h2>
          <p>I’m Hosanna, an experienced Art Director and Graphic Designer, based in the Highest (yep, the top floor of my Montréal condo).
          <br/><br/>
          I'm a full-time freelancer, with a strong focus on Brand Identity solutions and CPG packaging. Throughout my career, I’ve had the privilege of working on diverse projects, from large-scale brands to boutique productions.
          <br/><br/>
          I know this sounds cheesy, but I really do work with love, and my creative process is all about transparency. Trust me, you’ll notice that in every project we navigate together.
          <br/><br/>
          For more specific blah blah blah, I invite you to check out my profile and connect on <a :href="linkedInUrl" target="_blank">LinkedIn</a>.
          <br/><br/>
          En français SVP... Vu que j'habite au Québec, La seule Province de la langue franglaise en Amérique du Nord, Je ne te niaise pas quand je dis: Je parle français aussi.
          <br/><br/>
          Se habla español... Si prefieres comunicarte con verdaderas erres y eñes. Porfa avisame, también hablo perfecto español.
          <br/><br/>
          Even if what you're looking for isn’t in <a :href="dribbbleUrl" target="_blank">MY PORTFOLIO</a>, don’t be shy! Email me, and let's see how we can elevate your project to new heights! :)</p>
        </article>
      </div>
    </div>
  </dialog>
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
