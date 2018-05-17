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
          <div class='col-4'>GOSI</div>
          <div class='col-4'>&nbsp;</div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' class='bold' inverted color='warning' v-model="gosivalue" disable/></q-field>
          </div>
          <div class='col-4'>Other deductions</div>
          <div class='col-4'>&nbsp;</div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' class='bold' inverted color='negative' v-model="deductions" /></q-field>
          </div>
          <div class='col-4'>Absence days</div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' class='bold' inverted color='info' v-model="absence" /></q-field>
          </div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' disable class='bold' inverted color='warning' v-model="absencevalue" /></q-field>
          </div>
          <div class='col-4'>OT1 (Hrs) 125%</div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' class='bold' inverted color='info' v-model="ot1" /></q-field>
          </div>
          <div class='col-4'>
            <q-field>
              <q-input type='number' disable class='bold' inverted color='tertiary' v-model="ot1value" /></q-field>
          </div>
          <div class='col-4'>OT2 (Hrs) 150%</div>
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
      deductions: null,
      absence: null,
      ot1: null,
      ot2: null
    };
  },
  computed: {
    gosivalue() {
      if (this.basic) {
        var value = parseFloat(this.basic) * 0.06;
        return value.toFixed(4);
      }
    },
    absencevalue() {
      if (this.basic && this.absence) {
        var value =
          parseFloat(this.basic) / 30 * parseFloat(this.absence);
        return value.toFixed(4);
      }
    },
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
      if (this.deductions) total -= parseFloat(this.deductions);
      if (this.gosivalue) total -= parseFloat(this.gosivalue);
      if (this.absencevalue) total -= parseFloat(this.absencevalue);
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

