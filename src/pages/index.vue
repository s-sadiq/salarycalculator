<template>
  <q-page class="flex flex-center">
    <div class='row justify-center'>
      <div class='col-xs-12 col-md-5 col-lg-4 q-pa-sm'>
        <div class='row'>
          <div class='col-4'>Basic salary</div>
          <div class='col-4'>&nbsp;</div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' class='bold' inverted color='info' v-model="basic" /></q-field>
          </div>
          <div class='col-4'>Allowences</div>
          <div class='col-4'>&nbsp;</div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' class='bold' inverted color='info' v-model="allowences" /></q-field>
          </div>
          <div class='col-4'>OT(1hr) 125%</div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' class='bold' inverted color='info' v-model="ot1" /></q-field>
          </div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' disable class='bold' inverted color='tertiary' v-model="ot1value" /></q-field>
          </div>
          <div class='col-4'>OT(2hrs) 150%</div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' class='bold' inverted color='info' v-model="ot2" /></q-field>
          </div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' disable class='bold' inverted color='tertiary' v-model="ot2value" /></q-field>
          </div>
          <div class='col-4'>Total salary</div>
          <div class='col-4'>&nbsp;</div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' disable class='bold' inverted color='positive' v-model="total" /></q-field>
          </div>
        </div>
      </div>
    </div>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: "salaryPage",
  data() {
    return {
      basic: null,
      allowences: null,
      ot1: null,
      ot2: null
    };
  },
  computed: {
    ot1value() {
      if (this.basic && this.ot1) {
        var value =
          parseFloat(this.basic) / 30 / 8 * 1.25 * parseFloat(this.ot1);
        return value.toFixed(4);
      }
    },
    ot2value() {
      if (this.basic && this.ot2) {
        var value =
          parseFloat(this.basic) / 30 / 8 * 1.5 * parseFloat(this.ot2);
        return value.toFixed(4);
      }
    },
    total() {
      var total = 0;
      if (this.basic) total += parseFloat(this.basic);
      if (this.allowences) total += parseFloat(this.allowences);
      if (this.ot1value) total += parseFloat(this.ot1value);
      if (this.ot2value) total += parseFloat(this.ot2value);
      return total;
    }
  }
};
</script>

<style>
.col-4 {
  margin-top: 4px !important;
  padding: 3px;
}
</style>

