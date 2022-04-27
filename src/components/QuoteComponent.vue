<template>
  <section class="quote">
    <div class="quote-body">
      {{ quote.text }}
    </div>
    <div class="quote-author">
      {{ quote.author === null ? 'Unknown' : quote.author }}
    </div>
  </section>
</template>

<script>
export default {
  props: ["quote"],
};
</script>

<style lang="scss" scoped>
.quote {
  display: flex;
  position: relative;
  clear: both;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: flex-end;
  max-width: 800px;
  padding: 30px;
  margin: 0 auto;

  &-body {
    font-size: 25px;
    font-weight: 600;
    background-color: var(--dark);
    color: var(--lite);
    padding: 32px;
    border-radius: 30px 30px 0 30px;
  }
  &-author {
    background: var(--primary);
    color: var(--lite);
    padding: 5px 14px;
    border-radius: 30px;
    margin-left: -19px;
    position: relative;
    font-style: italic;
    font-size: 17px;
  }
}
</style>
