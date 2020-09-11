<template lang="html">
  <div :class="classNames.page">
    <div :class="classNames.formContainer">
      <div :class="classNames.formLogo">
         <img src="/logo.png" alt="logo">
      </div>
      <h1 :class="classNames.formH1"><span>We're</span> <div>coming</div> <div>soon</div> </h1>
      <p :class="classNames.formP">Hello fellow shoppers! We're currently building our new fashion store. Add your email below to stay up to date with announcements and our launch deals.</p>
      <form
        :class="classNames.form"
        @submit="handleSubmit">
          <input :class="classNames.formInput" type="text" v-model="email" placeholder="Email Address" />
          <input :class="classNames.formButton" type="submit" value=">"/>
      </form>
    </div>
    <div :class="classNames.pageHero">
        <img src="/hero.jpg" alt="hero">
    </div>
  </div>
</template>

<script>
import component from './script.kofu'

export default {
  ...component
}
</script>
