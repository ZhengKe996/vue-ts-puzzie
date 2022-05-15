<template>
  <div id="footer">
    <div class="footer__cover" />

    <div class="footer__text">
      <div>© 2022 Copyright:</div>

      <div>Timu 范正科</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
#footer {
  @include base__section-shadow;

  padding: 0.6rem;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  column-gap: 0.5rem;
  row-gap: 10px;
  position: relative;

  .footer__cover {
    @include base__cover;

    z-index: -1;
    background: $base__color--secondary;
    opacity: 0.9;
  }

  .footer__text {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: inherit;
  }
}
</style>
