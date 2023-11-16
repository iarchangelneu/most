<template>
  <div class="fullpage">
    <TheHeader />

    <NuxtPage />

    <TheFooter />
  </div>
</template>
<style lang="scss">
.fullpage {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100vh;
}

.ql-editor {
  height: 300px;
  /* Например, 300px */
}
</style>
<style>
.ql-editor {
  height: 250px !important;
  border-radius: 0 !important;
  color: #fff;
  font-size: 20px;
  font-style: normal;
  font-weight: 400;
  line-height: 130%;
  font-family: var(--int);
  /* Например, 300px */
}

.ql-editor {
  border: 1px solid #f00 !important;
  border-top-left-radius: 0 !important;
  border-top-right-radius: 0 !important;
}

.ql-container.ql-snow {
  border: 1px solid #f00 !important;
}

.ql-toolbar.ql-snow {
  border: 1px solid #f00 !important;
  border-radius: 0 !important;
  border-bottom-right-radius: 0 !important;
  border-bottom-left-radius: 0 !important;
}
</style>