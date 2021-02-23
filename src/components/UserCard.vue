<template>
  <div class="user">
    <div class="user__name">{{ $attrs.user.userName }}</div>
    <div class="user__position">{{ $attrs.user.userPosition }}</div>
    <div class="user__description">{{ $attrs.user.userDescription }}</div>
    <img class="user__avatar" src="~@/assets/user.png" alt="avatar" />
  </div>
</template>

<script>
export default {
  name: "UserCard",
};
</script>

<style lang="scss">
.user {
  padding-left: $card-padding;
  position: relative;
  flex: 0 0 15%;
  &__name {
    font-family: $fontFamily;
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 20px;
    color: $font-dark;
  }

  &__position {
    font-family: $fontFamily;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 20px;
    color: $font-light;
  }

  &__description {
    font-family: $fontFamily;
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 20px;
    color: $font-dark;
    background: $description-bg;
    padding: 5px 5px 10px 45px;
    margin-top: 5px;
    margin-left: -45px;
    border: 1px solid #dadada;
    border-radius: 5px;
  }

  &__avatar {
    position: absolute;
    left: -5px;
    top: -5px;
    width: 124px;
    height: 124px;
    border-radius: 50%;
  }
}
</style>