<template>
  <div class="rangeblock">
    <div class="rangeblock__title">Услуги</div>
    <hr />
    <div class="rangeblock__chart">
      <div
        v-for="item in $attrs.services"
        :key="item.name"
        :ref="item.name"
        :range="item.quantity"
      >
        <div class="rangeblock__chart_item">
          <span class="rangeblock__chart_item__name">{{ item.name }}</span>
          <span class="rangeblock__chart_item__quantity">{{
            item.quantity
          }}</span>
        </div>
      </div>
    </div>
    <hr />
    <div class="rangeblock__total">
      <span>Всего</span>
      <span>{{ totalServises }}</span>
    </div>
  </div>
</template>

<script>
import _variables from "./../styles/_variables.scss";

export default {
  name: "RangesBlock",
  data() {
    return {
      list: this.$attrs.services,
      totalServises: 0,
    };
  },
  methods: {
    totalServices(list) {
      //total number of services
      this.totalServises = list.reduce(
        (summ, item) => (summ += item.quantity),
        0
      );
    },
    getChartData(services) {
      //function to paint service range bars
      Object.keys(this.$refs).forEach((el) => {
        const persent = services / 100;
        const range = this.$refs[el][0].attributes.range.value / persent;
        const prefixes = ["-o-", "-ms-", "-moz-", "-webkit-"];
        const color =
          range > 50 ? _variables.range_greater : _variables.range_smaller;
        for (var i = 0; i < prefixes.length; i++) {
          this.$refs[el][0].children[0].style.background =
            prefixes[i] + `linear-gradient(0deg, ${color} ${range}%, #fff 0%)`;
        }
      });
    },
  },
  mounted() {
    this.totalServices(this.list);
    this.getChartData(this.totalServises);
  },
};
</script>

<style lang="scss">
.rangeblock {
  flex: 0 0 30%;
  width: 100%;
  padding: 5px 0;
  padding-left: $card-padding;
  &__title {
    width: 100%;
    text-align: right;
    padding: 7px;
    padding-right: 30px;
    font-family: $fontFamily;
    font-style: normal;
    font-weight: normal;
    font-size: 13px;
    line-height: 15px;
  }

  &__chart {
    width: 100%;
    padding: 10px 0;
    &_item {
      position: relative;
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 3px;
      padding-right: 38px;
      position: relative;
      margin: 2px 0;
      @media (max-width: 400px) {
        padding-right: 25px;
      }
      &__name {
        font-family: $fontFamily;
        font-style: normal;
        font-weight: normal;
        font-size: 13px;
        line-height: 20px;
        color: $font-dark;
      }
      &__quantity {
        font-family: $fontFamily;
        font-style: normal;
        font-weight: bold;
        font-size: 13px;
        line-height: 15px;
        color: $font-dark;
      }
      border-radius: 0px 3px 3px 0px;
    }
  }

  &__total {
    width: 100%;
    padding: 9px 38px 9px 0px;
    font-family: $fontFamily;
    color: $font-dark;
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 26px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    @media (max-width: 400px) {
      padding-right: 25px;
    }
  }
  hr {
    height: 1px;
    width: 100%;
    background: #dadada;
  }
}
</style>