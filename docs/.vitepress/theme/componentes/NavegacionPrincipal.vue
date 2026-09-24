<script setup>
import { isActive } from 'vitepress/dist/client/shared'
import { toRefs } from 'vue'
import pkg from '@centrogeomx/sisdai-mapas/package.json'

const props = defineProps(['nav', 'ruta'])
const { ruta } = toRefs(props)
</script>

<template>
  <SisdaiNavegacionPrincipal>
    <template #identidad>
      <a
        href="https://sisdai.org"
        target="_blank"
        rel="noopener noreferrer"
        class="nav-hiperviculo-logo"
      >
        <img
          :src="`/sisdai.png`"
          class="nav-logo color-invertir"
          alt="Sisdai."
        />
      </a>
    </template>
    <template #complementario>
      <div class="nav-menu-contenedor">
        <a
          class="nav-hipervinculo"
          href="https://sisdai.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          <b>IR A SISDAI</b>
        </a>
        <a
          class="nav-hipervinculo"
          href="https://gitlab.com/sisdai-org/sisdai-mapas"
          target="_blank"
          rel="noopener noreferrer"
          :aria-label="`Repositorio de código sisdai-mapas versión ${pkg.version}`"
        >
          <span
            class="pictograma-social-github m-r-1"
            aria-hidden="true"
          />
          <b aria-hidden="true">{{ `v${pkg.version}` }}</b>
        </a>
      </div>
    </template>

    <ul class="nav-menu">
      <li
        v-for="item in nav"
        :key="item.text"
      >
        <a
          class="nav-hipervinculo"
          :class="{
            'router-link-exact-active router-link-active': isActive(
              ruta,
              item.activeMatch || item.link,
              !!item.activeMatch
            ),
          }"
          :href="item.link"
          :target="item.target"
          :rel="item.rel"
        >
          {{ item.text }}
        </a>
      </li>
    </ul>
  </SisdaiNavegacionPrincipal>
</template>
