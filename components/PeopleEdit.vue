<template>
  <v-dialog
    v-model="dialog"
    width="542"
    overlay-color="var(--whisper)"
    content-class="rounded-dialog"
  >
    <v-card class="card pt-7 pb-10">
      <div class="pl-12 pr-8 d-flex justify-space-between align-center">
        <div class="title_h3">Information about {{ item.name }}</div>
        <div>
          <v-btn icon @click="onClose">
            <v-icon color="#909FBA"> mdi-close</v-icon>
          </v-btn>
        </div>
      </div>
      <v-card
        elevation="0"
        class="pl-12 pt-4 pr-8 d-flex justify-space-between align-center"
      >
        <v-btn color="indigo">Add tasks</v-btn>
        <v-btn color="indigo">Send Message</v-btn>
        <v-btn color="indigo">See Statistic</v-btn>

      </v-card>

      <v-card
        flat
        width="75%"
        class="mt-8 mx-12 pa-5 rounded-lg d-flex align-center"
      >
        <div class="mr-4">
          <img width="300" height="300" :src="item.image" alt=""/>
        </div>
      </v-card>
      <v-card
        elevation="0"
      width="75%"
      class="mt-2 mx-5  rounded-lg  align-center"
      >
        <div class="d-flex justify-space-between mx-10 py-2">
          <div class="data-text">
            <span class="text_h4 float-left">Name: </span>
            <span class="text-comet">{{ item.name }}</span>
          </div>
        </div>
        <div class="d-flex justify-space-between mx-10 py-2">
          <div class="data-text">
            <span class="text_h4 float-left">Email: </span>
            <span class="text-comet">{{ item.email }}</span>
          </div>
        </div>
        <div class="d-flex justify-space-between mx-10 py-2">
        <div class="data-text">
          <span class="text_h4 float-left">Mobile Number: </span>
          <span class="text-comet">{{ item.mobilePhone }}</span>
        </div>
      </div>
        <div class="d-flex justify-space-between mx-10 py-2">
          <div class="data-text">
            <span class="text_h4 float-left">Work from: </span>
            <span class="text-comet">{{ item.workStart }}</span>
          </div>
        </div>
      </v-card>
      <v-card
        class="mt-2 mx-5  rounded-lg  align-center"
      elevation="0"
      color="white"
      >
        <v-btn color="red" class="ma-8 float-end">Close</v-btn>
      </v-card>

      <!--      <div v-for="(report, i) in reports" :key="i">-->
      <!--        <v-divider class="divider"></v-divider>-->
      <!--        <div class="d-flex justify-space-between mx-10 py-2">-->
      <!--          <div class="data-text">-->
      <!--            <span class="mr-8">{{ report.year }}</span>-->
      <!--            <span>{{-->
      <!--                report.title + ` ${report.is_amendment ? 'Amendment' : ''}`-->
      <!--              }}</span>-->
      <!--          </div>-->
      <!--          <div class="data-text">-->
      <!--            <span>{{-->
      <!--                ` ${moment(new Date(report.date_filed)).format(-->
      <!--                  'MM-DD-YYYY, h:mm A',-->
      <!--                )}`-->
      <!--              }}</span>-->
      <!--            &lt;!&ndash;            <v-card class="elevation-0 chips">&ndash;&gt;-->
      <!--            &lt;!&ndash;              <div class="chips-text">{{ report.status }}</div>&ndash;&gt;-->
      <!--            &lt;!&ndash;            </v-card>&ndash;&gt;-->
      <!--          </div>-->
      <!--        </div>-->
      <!--        <v-divider v-if="i === reports.length - 1" class="divider"></v-divider>-->
      <!--      </div>-->
      <!--      <div class="text-center mt-10">-->
      <!--        <v-btn large class="cancel-button elevation-0" @click="onClose">-->
      <!--          <span class="cancel-text">Cancel</span>-->
      <!--        </v-btn>-->
      <!--        <EFButton class="mx-4" large @el-onclick="onSaveAndClose">-->
      <!--          {{ buttonName }}-->
      <!--        </EFButton>-->
      <!--      </div>-->
    </v-card>
  </v-dialog>
</template>

<script>
import moment from 'moment';

export default {
  components: {},
  props: {
    // parentComponent: {
    //   type: String,
    //   default: '',
    // },
    item: {
      type: Object,
      default: () => {
      },
    },
    // reportsToBeAmended: {
    //   type: Array,
    //   default: () => [],
    // },
  },
  data() {
    return {
      moment,
      reports: this.reportsToBeAmended,
      itemToBeDeletedEdited: this.item,
      dialog: true,
      buttonName: 'Confirm and save',
      title: '',
      subtitle: '',
    };
  },
  mounted() {
    // TODO: no amendment status here

    switch (this.parentComponent) {
      case 'counterparties':
        this.buttonName = 'Confirm Amendments';
        this.title =
          'Changes in this counterparty details will affect the data in the reports you have filed. Report Amendments will be created and should be filed accordingly.';
        this.subtitle = '';
        break;
      case 'accounts':
        this.title =
          'Changes in the committee details will affect the data in the reports you have filed. Report Amendments will be created and should be filed accordingly.';
        this.subtitle =
          'You will also need to sign and mail the amendment of <a href="https://s3.amazonaws.com/dl.ncsbe.gov/Campaign_Finance/Forms/cro2100A/ecro2100A.pdf" target="_blank">Statement of Organization</a> and new <a href="https://s3.amazonaws.com/dl.ncsbe.gov/Campaign_Finance/Forms/cro3500/ecro3500.pdf" target="_blank">Certification of Financial Account Information</a>.';
        this.buttonName = 'Save and Confirm';
        break;
      case 'committee':
        this.title =
          'Changes in the committee details will affect the data in the reports you have filed. Report Amendments will be created and should be filed accordingly.';
        this.subtitle =
          'You will also need to sign and mail the amendment of <a href="https://s3.amazonaws.com/dl.ncsbe.gov/Campaign_Finance/Forms/cro2100A/ecro2100A.pdf" target="_blank">Statement of Organization</a>.';
        this.buttonName = 'Save and Confirm';
        break;
      default:
        this.buttonName = 'Confirm and save';
        this.subtitle = '';
        this.title =
          'Changes in this transaction will affect the data in the reports you have filed. Report Amendments will be created and should be filed accordingly.';
        break;
    }
  },
  methods: {
    onClose() {
      // TODO: FIX closeAmendmentDialog does not work for Counterparty
      this.$nuxt.$emit('closeAmendmentDialog');
      this.$nuxt.$emit('closeAmendmentDialogCounterparty');
    },
    onSaveAndClose() {
      this.$nuxt.$emit(
        'saveAndCloseAmendmentDialog',
        this.itemToBeDeletedEdited,
      );
      // TODO: FIX saveAndCloseAmendmentDialog does not work for Counterparty
      this.$nuxt.$emit(
        'saveAndCloseAmendmentDialogCounterparty',
        this.itemToBeDeletedEdited,
      );
    },
  },
};
</script>
<style lang="scss" scoped>
.text-comet {
  color: var(--comet);
}

.filed-column-dialog {
  width: 146px;
}

.card {
  box-shadow: 4px 4px 28px rgba(144, 159, 186, 0.1) !important;
}

.title_h3 {
  font-family: var(--font-family-page-title);
  font-style: normal;
  font-weight: bold;
  font-size: 18px;
  line-height: 22px;
  /* identical to box height */

  /* Biscay */

  color: var(--biscay);
}

.text_h4 {
  font-style: normal;
  font-weight: bold;
  font-size: 16px;
  line-height: 19px;
  text-align: center;
  /* Biscay */

  color: var(--biscay);
}

.chips {
  background: rgba(22, 200, 157, 0.09);
  border-radius: 6px;
  padding: 8px;
}

.chips-text {
  font-family: var(--font-family-page-title);
  font-style: normal;
  font-weight: bold;
  font-size: 10px;
  line-height: 10px;
  /* identical to box height, or 100% */

  text-align: center;
  letter-spacing: 0.03em;
  text-transform: uppercase;

  /* Java */

  color: #20c9a0;
}

.divider {
  border-color: #eff3f9 !important;
}

.data-text {
  font-family: var(--font-family-callout);
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 22px;
  /* identical to box height, or 160% */

  letter-spacing: 0.02em;
  font-feature-settings: 'tnum' on, 'lnum' on;

  /* Big Stone */

  color: var(--big-stone);
}

::v-deep {
  .subtext {
    font-family: var(--font-family-callout);
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 22px;
    letter-spacing: 0.02em;
    /* Black Pearl */

    color: var(--black-pearl);

    a {
      color: var(--dodger-blue);
    }
  }
}

.cancel-button {
  background-color: white !important;
  border: 2px solid var(--mystic);
  border-radius: 9px;
}

.cancel-text {
  font-family: var(--font-family-page-title);
  font-style: normal;
  font-weight: bold;
  font-size: 14px;
  line-height: 16px;
  /* identical to box height, or 114% */

  text-align: center;
  letter-spacing: 0.02em;
  text-transform: uppercase;

  /* Biscay */

  color: var(--biscay);
}
</style>
