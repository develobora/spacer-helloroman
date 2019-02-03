<template>
  <div class="claim-wrapper">
    <h1 class="claim">
      Spacer
    </h1>
    <p class="subclaim">
      Begin your journey through our amazing galaxy,
      and discover places you never even heard of.
    </p>
    <p class="subclaim">
      Type anything space-related to start.
    </p>
  </div>
</template>

<script>

export default {
  name: 'Claim',
};

</script>

<style lang="scss" scoped>
  @import '~@/scss/settings';

  .claim-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    color: white;
  }

  .claim {
    font-size: 50px;
    margin: 0;
    text-transform: uppercase;

    @media (min-width: $screen-sm) {
      font-size: 80px;
    }

    @media (min-width: $screen-md) {
      font-size: 100px;
      letter-spacing: 4px;
    }
  }

  .subclaim {
    margin: 20px 0 0 0;
    font-size: 13px;
    font-weight: 400;

    @media (min-width: $screen-sm) {
      width: 500px;
      font-size: 17px;
      line-height: 1;
      letter-spacing: 1px;
    }
  }
</style>
