<template>
  <div class="user-block">
    <div class="user-block__main">
      <UserCardVue :user="user" />
      <RangesBlockVue :services="userServices" />
      <CommentsBlockVue :comments="visitorComments" />
    </div>
    <div class="user-block__footer">
      <form class="user-block__footer_form" @submit.prevent="addNewComment">
        <p>
          <textarea
            class="user-block__footer_textarea"
            name="message"
            v-model="message"
            v-on:keyup.enter="keyboardHandler"
          />
        </p>
        <p>
          <button
            class="user-block__footer_submit"
            type="submit"
            name="message"
          >
            Написать консультанту
          </button>
        </p>
      </form>
    </div>
  </div>
</template>

<script>
import CommentsBlockVue from "./CommentsBlock.vue";
import RangesBlockVue from "./RangesBlock.vue";
import UserCardVue from "./UserCard.vue";
export default {
  name: "UserBlock",
  components: {
    UserCardVue,
    RangesBlockVue,
    CommentsBlockVue,
  },
  data() {
    return {
      message: "",
      inputName: "Test Name",
      user: {
        avatar: "~@/assets/user.png",
        userName: "Вероника Ростова",
        userPosition: "Менеджер по продажам",
        userDescription:
          "Подберу для вас самые лучшие предложения. Мои услуги абсолютно бесплатны",
      },
      userServices: [
        {
          name: "Ручное бронирование",
          quantity: 11,
        },
        {
          name: "Пакетные туры",
          quantity: 3,
        },
        {
          name: "Отели",
          quantity: 1,
        },
      ],
      visitorComments: {
        likes: 131,
        commentsTotal: 14,
        comments: [
          {
            name: "Самуил",
            date: "13 октября 2011",
            text: "Привет, Верунь! ниче себе ты крутая. фотка класс!!!! ",
          },
          {
            name: "Лилия Семёновна ",
            date: "14 октября 2011",
            text:
              "Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент, это и есть всемирно известный центр огранки алмазов и торговли бриллиантами?",
          },
          {
            name: "Лилия Семёновна ",
            date: "14 октября 2011",
            text:
              "Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент?",
          },
          {
            name: "Лилия Семёновна ",
            date: "14 октября 2011",
            text:
              "Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент?",
          },
          {
            name: "Лилия Семёновна ",
            date: "14 октября 2011",
            text:
              "Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент?",
          },
        ],
      },
    };
  },
  methods: {
    keyboardHandler(e) {
      e.ctrlKey ? this.addNewComment() : null;
    },
    addNewComment() {
      let today = new Date();
      let dd = String(today.getDate()).padStart(2, "0");
      let mm = String(today.getMonth() + 1).padStart(2, "0");
      let yyyy = today.getFullYear();
      today = `${dd} ${mm} ${yyyy}`;
      if (this.message.length) {
        this.visitorComments.comments.push({
          name: this.inputName,
          date: today,
          text: this.message,
        });
      }
      this.message = "";
    },
  },
};
</script>

<style lang="scss" >
.user-block {
  position: relative;
  min-height: 500px;
  max-height: 900px;
  height: auto;
  max-width: 720px;
  width: 100%;
  background: $main-bg;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  &__main {
    width: 100%;
    padding: $body-padding;
    position: relative;

    flex: 0 0 80%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-end;
  }
  &__footer {
    flex: 0 0 20%;
    width: 100%;
    background: $footer-bg;
    padding: $footer-padding;
    text-align: center;
    &_form {
    }
    &_textarea {
      min-width: 100%;
      max-width: 100%;
      min-height: 60px;
      max-height: 80px;
      margin-bottom: 15px;
      padding: 10px;
      &:focus {
        outline: auto;
      }
    }
    &_submit {
      background: $send-button-bg;
      padding: 15px 70px;
      border-radius: 23px;
      font-size: 14px;
      font-weight: 700;
      &:hover {
        background: darken($send-button-bg, 10%);
        -webkit-background: darken($send-button-bg, 10%);
        -moz-background: darken($send-button-bg, 10%);
        -ms-background: darken($send-button-bg, 10%);
        -o-background: darken($send-button-bg, 10%);
      }
      @media (max-width: 335px) {
        padding: 15px 40px;
      }
    }
  }
}
</style>