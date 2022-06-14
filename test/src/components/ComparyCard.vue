<template>
  <div class="main">
    <div class="header">
      <div class="header-text">
        <h1 class="color-navy text-28px fw-800">
          Simple, traffic-based pricing
        </h1>
        <h3 class="text-muted fw-600 text-15px">
          Sign-up for our 30-day trial. No credit card required.
        </h3>
      </div>
      <img class="header-img" src="../assets/pattern-circles.svg" />
    </div>
    <div class="card">
      <div class="card-header">
        <h1 class="text-muted text-14px fw-800 pageviews">
          {{ pageViews }} PAGEVIEWS
        </h1>
        <h1 class="text-40px color-navy fw-800 price">
          ${{ isDiscount ? (billing * 0.75).toFixed(2) : billing.toFixed(2) }}
          <span class="text-muted text-16px"> / month</span>
        </h1>
        <input
          class="styled-slider slider-progress"
          type="range"
          id="price-range"
          min="1"
          max="5"
          v-model.number="priceRange"
          @change="checkPriceRange($event)"
        />
      </div>
      <div class="card-body">
        <div class="infoBilling">
          <div class="text-muted text-12px item1">Monthly Billing</div>
          <label class="switch item2">
            <input type="checkbox" v-model="isDiscount" />
            <span class="slider round"></span>
          </label>
          <div class="text-muted text-12px item3">Yearly Billing</div>
          <div class="billingDiscount text-10px item4">25% discount</div>
          <div class="billingDiscountMobile text-10px item4">-25%</div>
        </div>
      </div>
      <hr />
      <div class="card-footer">
        <div class="checks">
          <p class="text-muted text-12px card-footer-item">
            <span class="checkedInfo"></span>Unlimited websites
          </p>
          <p class="text-muted text-12px card-footer-item">
            <span class="checkedInfo"></span>100% data ownership
          </p>
          <p class="text-muted text-12px card-footer-item">
            <span class="checkedInfo"></span>Email reports
          </p>
        </div>
        <div class="submit-container">
          <input
            class="form-submit-input text-12px"
            type="button"
            value="Start my trial"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ComparyCard",
  data() {
    return {
      priceRange: 3,
      pageViews: "100K",
      billing: null,
      isDiscount: false,
      billingDiscount: "25% discount",
    };
  },
  created() {
    this.checkPriceRange(null);
  },
  mounted() {
    for (let e of document.querySelectorAll(
      'input[type="range"].slider-progress'
    )) {
      e.style.setProperty("--value", e.value);
      e.style.setProperty("--min", e.min == "" ? "0" : e.min);
      e.style.setProperty("--max", e.max == "" ? "100" : e.max);
      e.addEventListener("input", () =>
        e.style.setProperty("--value", e.value)
      );
    }
  },
  methods: {
    checkPriceRange() {
      switch (this.priceRange) {
        case 1:
          this.pageViews = "10K";
          this.billing = 8;
          break;
        case 2:
          this.pageViews = "50K";
          this.billing = 12;
          break;
        case 3:
          this.pageViews = "100K";
          this.billing = 16;
          break;
        case 4:
          this.pageViews = "500K";
          this.billing = 24;
          break;
        case 5:
          this.pageViews = "1M";
          this.billing = 36;
          break;
        default:
          break;
      }
    },
  },
};
</script>



