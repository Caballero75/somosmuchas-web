<template>
  <div class="que-pasa-box">
    <div class="texto-descriptivo">
      <h1 class="title is-1 has-text-white has-text-weight-bold mb-2">
        {{ title }}
      </h1>
      <p class="is-size-5">
        {{ description }}
      </p>
    </div>
    <slot />
    <NuxtLink v-if="to" :to="to" class="button is-primary has-text-weight-bold is-rounded enter-button is-medium">
      ENTRAR
    </NuxtLink>
    <a v-if="href" :href="href" target="_blank" class="button is-primary has-text-weight-bold is-rounded enter-button is-medium">
      ENTRAR
    </a>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: true
    },
    to: {
      type: String,
      required: false,
      default: null
    },
    href: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
.que-pasa-box{
  height: 250px;
  margin: 10px;
  border: 2px solid $secondary;
  position: relative;
  &:hover{
    .texto-descriptivo{
      opacity: 1;
    }
  }
  img {
  max-height: 60%;
  max-width: 75%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 50;
}
.enter-button{
  position: absolute;
  bottom: -20px;
  left: 50%;
  transform: translate(-50%, 0);
  z-index: 150;
  &:hover{
    color: $primary;
    background-color: white;
    border: 2px solid $primary;
  }
}
.texto-descriptivo{
  position: absolute;
  padding: 30px;
  background-color: rgba(darken($secondary,20%), 0.8);
  height: 100%;
  opacity: 0;
  color: #FFF;
  text-shadow: 1px 1px 1px rgba(0,0,0,0.6);
  transition: opacity .2s ease-out;
  -moz-transition: opacity .2s ease-out;
  -webkit-transition: opacity .2s ease-out;
  -o-transition: opacity .2s ease-out;
  font-size: $size-5;
  overflow-y: hidden;
  z-index: 100;
}
}
</style>
