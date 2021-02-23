<template>
  <div class="comments-block">
    <div class="comments-block__title">
      <div class="comments-block__title_text">
        <span>Последние отзывы</span>
        <a href="#">Все отзывы</a>
      </div>
      <div class="comments-block__title_icons">
        <span class="likes">{{ $attrs.comments.likes }}</span>
        <span class="total">{{ $attrs.comments.commentsTotal }}</span>
      </div>
    </div>
    <div class="comments-block__wrapper">
      <div v-for="(comment, index) in $attrs.comments.comments" :key="index">
        <div class="comment">
          <div class="comment__title">
            <span class="comment__title_name">{{ comment.name }}</span>
            <small class="comment__title_date">{{ comment.date }}</small>
          </div>
          <div class="comment__body">
            {{ comment.text }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CommentsBlock",
};
</script>

<style lang="scss">
.comments-block {
  flex: 0 0 50%;
  position: relative;
  width: 100%;
  &__title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 6px 0;
    @media (max-width: 400px) {
      flex-direction: column;
    }
    &_text {
      span {
        font-family: $fontFamily;
        font-style: normal;
        font-weight: bold;
        font-size: 16px;
        line-height: 16px;
        color: $font-dark;
        margin-right: 20px;
      }
      a {
        font-family: $fontFamily;
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 16px;
        color: $font-link;
        &:hover {
          border-bottom: 1px solid;
        }
      }
    }

    &_icons {
      span {
        margin-left: 10px;
        padding: 0 0 0 20px;
        font-family: $fontFamily;
        font-style: normal;
        font-weight: normal;
        color: $font-dark;
        font-size: 12px;
        line-height: 14px;
      }
    }
  }

  &__wrapper {
    overflow-y: scroll;
    height: 360px;
  }
}
.likes {
  position: relative;
  &::after {
    content: "";
    position: absolute;
    height: 16px;
    width: 16px;
    top: 0;
    left: 0;
    background: center / contain no-repeat url("~@/assets/likes.png");
  }
}
.total {
  position: relative;
  &::after {
    content: "";
    position: absolute;
    height: 16px;
    width: 16px;
    top: 0;
    left: 0;
    background: center / contain no-repeat url("~@/assets/comment.png");
  }
}
.comment {
  &__title {
    padding: 10px 0 10px 0;
    &_name {
      font-family: $fontFamily;
      font-style: normal;
      font-weight: bold;
      font-size: 14px;
      line-height: 19px;
      color: $font-dark;
      margin-right: 10px;
    }

    &_date {
      color: $font-light;
      font-size: 11px;
    }
  }

  &__body {
    font-family: $fontFamily;
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 19px;
    color: $font-dark;
    background: $comment-bg;
    padding: 15px;
    border: 1px solid #c4cbcf;
    box-shadow: 0px 4px 10px rgba(128, 128, 128, 0.1);
  }
}
</style>
