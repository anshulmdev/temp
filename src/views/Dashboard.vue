<template>
  <div v-if="$store.state.firestoreData">
    <!-- Hero -->
    <div class="bg-body-light">
      <div class="content content-full">
        <div
          class="d-flex flex-column flex-sm-row justify-content-sm-between align-items-sm-center py-2 text-center text-sm-left"
        >
          <div class="flex-sm-fill">
            <h1 class="h3 font-w700 mb-2">Main Dashboard</h1>
            <h2 class="h6 font-w500 text-muted mb-0">
              Welcome
              <a class="font-w600" href="javascript:void(0)">{{
                $store.state.firestoreData.name.split(" ")[0]
              }}</a
              >, everything looks great.
            </h2>
          </div>
          <div class="mt-3 mt-sm-0 ml-sm-3">
            <router-link to="/backend/main/assignment">
              <b-button
                variant="alt-primary"
                class="mr-1"
                href="javascript:void(0)"
                v-click-ripple
              >
                <i class="fa fa-plus-square mr-1"></i> New Assignment
              </b-button>
            </router-link>
          </div>
        </div>
      </div>
    </div>
    <!-- END Hero -->

    <!-- Page Content -->
    <div class="content">
      <!-- Stats -->
      <b-row>
        <b-col cols="6" md="3" lg="6" xl="3">
          <base-block
            tag="a"
            rounded
            link-pop
            content-class="d-flex py-4"
            href="javascript:void(0)"
          >
            <div class="flex-grow-1">
              <div class="font-size-sm font-w600 text-uppercase text-muted">
                Applications
              </div>
              <div class="font-size-h3">
                {{ $store.state.firestoreData.candidates.applied.length }}
              </div>
            </div>
            <div class="d-flex ml-2">
              <div class="flex-grow-1 px-1 bg-success-light rounded-lg"></div>
            </div>
          </base-block>
        </b-col>
        <b-col cols="6" md="3" lg="6" xl="3">
          <base-block
            tag="a"
            rounded
            link-pop
            content-class="d-flex py-4"
            href="javascript:void(0)"
          >
            <div class="flex-grow-1">
              <div class="font-size-sm font-w600 text-uppercase text-muted">
                Invited
              </div>
              <div class="font-size-h3">
                {{ $store.state.firestoreData.candidates.invited.length }}
              </div>
            </div>
            <div class="d-flex ml-2">
              <div class="flex-grow-1 px-1 bg-danger-light rounded-lg"></div>
            </div>
          </base-block>
        </b-col>
        <b-col cols="6" md="3" lg="6" xl="3">
          <base-block
            tag="a"
            rounded
            link-pop
            content-class="d-flex py-4"
            href="javascript:void(0)"
          >
            <div class="flex-grow-1">
              <div class="font-size-sm font-w600 text-uppercase text-muted">
                Test Conducted
              </div>
              <div class="font-size-h3">
                {{ $store.state.firestoreData.candidates.completed.length }}
              </div>
            </div>
            <div class="d-flex ml-2">
              <div class="flex-grow-1 px-1 bg-success-light rounded-lg"></div>
            </div>
          </base-block>
        </b-col>
        <b-col cols="6" md="3" lg="6" xl="3">
          <base-block
            tag="a"
            rounded
            link-pop
            content-class="d-flex py-4"
            href="javascript:void(0)"
          >
            <div class="flex-grow-1">
              <div class="font-size-sm font-w600 text-uppercase text-muted">
                Shortlisted
              </div>
              <div class="font-size-h3">
                {{ $store.state.firestoreData.candidates.shortlisted.length }}
              </div>
            </div>
            <div class="d-flex ml-2">
              <div class="flex-grow-1 px-1 bg-danger-light rounded-lg"></div>
            </div>
          </base-block>
        </b-col>
      </b-row>
      <!-- END Stats -->

      <!-- END Dashboard Charts -->

      <!-- Customers and Latest Orders -->
      <b-row class="row-deck">
        <!-- Latest Customers -->
        <!-- Latest Orders -->
        <b-col xl="6">
          <base-block
            rounded
            title="Ongoing Assignments"
            header-bg
            content-full
          >
            <template #options>
              <button type="button" class="btn-block-option">
                <i class="si si-settings"></i>
              </button>
            </template>
            <b-table-simple
              striped
              hover
              borderless
              class="table-vcenter font-size-sm mb-0"
            >
              <b-thead>
                <b-tr>
                  <b-th class="font-w700">ID</b-th>
                  <b-th class="d-none d-sm-table-cell font-w700">Name</b-th>
                  <b-th class="font-w700">Tag</b-th>
                  <b-th
                    class="d-none d-sm-table-cell font-w700 text-center"
                    style="width: 120px"
                    >Score</b-th
                  >
                  <b-th
                    class="font-w700 text-center"
                    style="width: 60px"
                  ></b-th>
                </b-tr>
              </b-thead>
              <b-tbody>
                <b-tr
                  v-for="(order, index) in $store.state.firestoreData.candidates
                    .ongoing"
                  :key="index"
                >
                  <b-td>
                    <a class="font-w600" href="javascript:void(0)"
                      ># {{ index }}</a
                    >
                  </b-td>
                  <b-td class="d-none d-sm-table-cell">
                    {{ order.name }}
                  </b-td>
                  <b-td>
                    <b-row v-for="(value, index) in order.tags" :key="index">
                      <b-col class="col-lg-4">
                        <b-badge :variant="index">{{ value }}</b-badge></b-col
                      >
                    </b-row>
                  </b-td>
                  <b-td class="d-none d-sm-table-cell text-center">
                    {{ order.score }}
                  </b-td>
                  <b-td class="text-center">
                    <a
                      v-b-modal.modal-block-extra-large
                      @click="url = order.resume"
                      href="javascript:void(0)"
                      v-b-tooltip.hover.nofade.left="'View Resume'"
                    >
                      <i class="fa fa-fw fa-clock"></i>
                    </a>
                  </b-td>
                </b-tr>
              </b-tbody>
            </b-table-simple>
          </base-block>
        </b-col>
        <!-- END Latest Orders -->
        <!-- Extra Large Block Modal -->
        <b-modal
          id="modal-block-extra-large"
          size="xl"
          body-class="p-0"
          hide-footer
          hide-header
        >
          <div class="block block-rounded block-themed block-transparent mb-0">
            <div class="block-header bg-primary-dark">
              <h3 class="block-title">Modal Title</h3>
              <div class="block-options">
                <button
                  type="button"
                  class="btn-block-option"
                  @click="$bvModal.hide('modal-block-extra-large')"
                >
                  <i class="fa fa-fw fa-times"></i>
                </button>
              </div>
            </div>
            <div class="block-content font-size-sm">
              <iframe :src="url" width="100%" height="600"> </iframe>
            </div>
            <div class="block-content block-content-full text-right border-top">
              <b-button
                variant="alt-success"
                class="mr-1"
                @click="$bvModal.hide('modal-block-extra-large')"
                >Close</b-button
              >
              <b-button
                variant="success"
                @click="$bvModal.hide('modal-block-extra-large')"
                >Ok</b-button
              >
            </div>
          </div>
        </b-modal>
        <!-- END Extra Large Block Modal -->
        <b-col xl="6">
          <base-block rounded title="Recent Shortlisted" header-bg content-full>
            <template #options>
              <button type="button" class="btn-block-option">
                <i class="si si-settings"></i>
              </button>
            </template>
            <b-table-simple
              striped
              hover
              borderless
              class="table-vcenter font-size-sm mb-0"
            >
              <b-thead>
                <b-tr>
                  <b-th class="font-w700">ID</b-th>
                  <b-th class="d-none d-lg-table-cell font-w700 text-center"
                    >Resume</b-th
                  >
                  <b-th class="font-w700">Name</b-th>
                  <b-th class="d-none d-sm-table-cell font-w700 text-center"
                    >Score</b-th
                  >
                  <b-th class="d-none d-sm-table-cell font-w700 text-center"
                    >Date</b-th
                  >
                  <b-th class="font-w700 text-center"></b-th>
                </b-tr>
              </b-thead>
              <b-tbody>
                <b-tr
                  v-for="(completed, index) in $store.state.firestoreData
                    .candidates.shortlisted"
                  :key="index"
                >
                  <b-td class="font-w600">
                    {{ index }}
                  </b-td>
                  <b-td class="d-none d-sm-table-cell text-center">
                    <a
                      v-b-modal.modal-block-extra-large2
                      @click="url = completed.resume"
                    >
                      <img
                        class="img-avatar img-avatar32"
                        src="img/avatars/avatar12.jpg"
                        alt="Avatar"
                    /></a>
                  </b-td>
                  <b-td>
                    <a class="link-fx font-w600" href="javascript:void(0)">{{
                      completed.name
                    }}</a>
                  </b-td>
                  <b-td class="d-none d-sm-table-cell text-center">
                    <a class="link-fx font-w600" href="javascript:void(0)">{{
                      completed.score
                    }}</a>
                  </b-td>
                  <b-td class="d-none d-sm-table-cell text-center">
                    <a class="link-fx font-w600" href="javascript:void(0)">{{
                      completed.time
                    }}</a>
                  </b-td>
                  <b-td class="text-center">
                    <a
                      href="javascript:void(0)"
                      v-b-tooltip.hover.nofade.left="'Invite for Interview'"
                    >
                      <i class="fa fa-fw fa-envelope"></i>
                    </a>
                  </b-td>
                </b-tr>
              </b-tbody>
            </b-table-simple>
          </base-block>
        </b-col>
        <!-- END Latest Customers -->
      </b-row>
      <!-- END Customers and Latest Orders -->
      <!-- Extra Large Block Modal -->
      <b-modal
        id="modal-block-extra-large2"
        size="xl"
        body-class="p-0"
        hide-footer
        hide-header
      >
        <div class="block block-rounded block-themed block-transparent mb-0">
          <div class="block-header bg-primary-dark">
            <h3 class="block-title">Modal Title</h3>
            <div class="block-options">
              <button
                type="button"
                class="btn-block-option"
                @click="$bvModal.hide('modal-block-extra-large')"
              >
                <i class="fa fa-fw fa-times"></i>
              </button>
            </div>
          </div>
          <div class="block-content font-size-sm">
            <iframe :src="url" width="100%" height="600"> </iframe>
          </div>
          <div class="block-content block-content-full text-right border-top">
            <b-button
              variant="alt-success"
              class="mr-1"
              @click="$bvModal.hide('modal-block-extra-large')"
              >Close</b-button
            >
            <b-button
              variant="success"
              @click="$bvModal.hide('modal-block-extra-large')"
              >Ok</b-button
            >
          </div>
        </div>
      </b-modal>
      <!-- END Extra Large Block Modal -->

      <!-- Dashboard Charts -->
      <b-row>
        <b-col lg="6">
          <!-- Earnings Chart -->
          <base-block rounded title="Language Trend" header-bg>
            <template #options>
              <button type="button" class="btn-block-option">
                <i class="si si-settings"></i>
              </button>
            </template>
            <template #content>
              <div class="block-content p-0">
                <div class="pt-3">
                  <chartjs-line
                    :chart-data="chartjsEarningsData"
                    :options="chartjsEarningsOptions"
                    :styles="chartjsStyles"
                  ></chartjs-line>
                </div>
              </div>
              <div class="block-content">
                <b-row class="items-push text-center py-3">
                  <b-col cols="6" xl="3">
                    <i class="fab fa-js fa-2x opacity-50"></i>
                    <p class="font-size-sm font-w500 text-muted mt-3 mb-0">
                      JavaScript
                    </p>
                  </b-col>
                  <b-col cols="6" xl="3">
                    <i class="fab fa-html5 fa-2x opacity-50"></i>
                    <p class="font-size-sm font-w500 text-muted mt-3 mb-0">
                      HTML/CSS
                    </p>
                  </b-col>
                  <b-col cols="6" xl="3">
                    <i class="fab fa-python fa-2x opacity-50"></i>
                    <p class="font-size-sm font-w500 text-muted mt-3 mb-0">
                      Python
                    </p>
                  </b-col>
                  <b-col cols="6" xl="3">
                    <i class="fab fa-java fa-2x opacity-50"></i>
                    <p class="font-size-sm font-w500 text-muted mt-3 mb-0">
                      Java
                    </p>
                  </b-col>
                </b-row>
              </div>
            </template>
          </base-block>
          <!-- END Earnings Chart -->
        </b-col>
        <b-col lg="6">
          <!-- Sales Chart -->
          <base-block rounded title="Language Trend" header-bg>
            <template #options>
              <button type="button" class="btn-block-option">
                <i class="si si-settings"></i>
              </button>
            </template>
            <template #content>
              <div class="block-content p-0">
                <div class="pt-3">
                  <chartjs-line
                    :chart-data="chartjsSalesData"
                    :options="chartjsSalesOptions"
                    :styles="chartjsStyles"
                  ></chartjs-line>
                </div>
              </div>
              <div class="block-content">
                <b-row class="items-push text-center py-3">
                  <b-col cols="6" xl="3">
                    <i class="fa fa-user-check fa-2x opacity-50"></i>
                    <p class="font-size-sm font-w500 text-muted mt-3 mb-0">
                      Shortlisted
                    </p>
                  </b-col>
                  <b-col cols="6" xl="3">
                    <i class="fa fa-user-cog fa-2x opacity-50"></i>
                    <p class="font-size-sm font-w500 text-muted mt-3 mb-0">
                      Waiting
                    </p>
                  </b-col>
                  <b-col cols="6" xl="3">
                    <i class="fa fa-users fa-2x opacity-50"></i>
                    <p class="font-size-sm font-w500 text-muted mt-3 mb-0">
                      Total
                    </p>
                  </b-col>
                  <b-col cols="6" xl="3">
                    <i class="fa fa-user-injured fa-2x opacity-50"></i>
                    <p class="font-size-sm font-w500 text-muted mt-3 mb-0">
                      Rejected
                    </p>
                  </b-col>
                </b-row>
              </div>
            </template>
          </base-block>
          <!-- END Sales Chart -->
        </b-col>
      </b-row>
    </div>
    <!-- END Page Content -->
  </div>
</template>

<script>
// Chart.js, https://www.chartjs.org
import Chart from "chart.js";

// Line Chart component using Vue Chart.js, for more info and examples you can check out https://github.com/apertureless/vue-chartjs
import ChartjsLine from "@/components/Chartjs/Line";

export default {
  components: {
    ChartjsLine,
  },
  data() {
    return {
      url: "https://static.thenounproject.com/png/543772-200.png",
      chartjsStyles: {
        position: "relative",
        height: "344px",
      },
      chartjsEarningsOptions: {
        maintainAspectRatio: false,
        scales: {
          yAxes: [
            {
              ticks: {
                suggestedMax: 3000,
              },
            },
          ],
        },
        tooltips: {
          intersect: false,
          callbacks: {
            label: (tooltipItems) => {
              return " $" + tooltipItems.yLabel;
            },
          },
        },
      },
      chartjsSalesOptions: {
        maintainAspectRatio: false,
        scales: {
          yAxes: [
            {
              ticks: {
                suggestedMax: 260,
              },
            },
          ],
        },
        tooltips: {
          intersect: false,
          callbacks: {
            label: (tooltipItems) => {
              return " " + tooltipItems.yLabel + " Sales";
            },
          },
        },
      },
      chartjsEarningsData: {
        labels: [
          "JAN",
          "FEB",
          "MAR",
          "APR",
          "MAY",
          "JUN",
          "JUL",
          "AUG",
          "SEP",
          "OCT",
          "NOV",
          "DEC",
        ],
        datasets: [
          {
            label: "This Year",
            fill: true,
            backgroundColor: "rgba(132, 94, 247, .3)",
            borderColor: "transparent",
            pointBackgroundColor: "rgba(132, 94, 247, 1)",
            pointBorderColor: "#fff",
            pointHoverBackgroundColor: "#fff",
            pointHoverBorderColor: "rgba(132, 94, 247, 1)",
            data: [
              2150,
              1350,
              1560,
              980,
              1260,
              1720,
              1115,
              1690,
              1870,
              2420,
              2100,
              2730,
            ],
          },
          {
            label: "Last Year",
            fill: true,
            backgroundColor: "rgba(233, 236, 239, 1)",
            borderColor: "transparent",
            pointBackgroundColor: "rgba(233, 236, 239, 1)",
            pointBorderColor: "#fff",
            pointHoverBackgroundColor: "#fff",
            pointHoverBorderColor: "rgba(233, 236, 239, 1)",
            data: [
              2200,
              1700,
              1100,
              1900,
              1680,
              2560,
              1340,
              1450,
              2000,
              2500,
              1550,
              1880,
            ],
          },
        ],
      },
      chartjsSalesData: {
        labels: [
          "JAN",
          "FEB",
          "MAR",
          "APR",
          "MAY",
          "JUN",
          "JUL",
          "AUG",
          "SEP",
          "OCT",
          "NOV",
          "DEC",
        ],
        datasets: [
          {
            label: "This Year",
            fill: true,
            backgroundColor: "rgba(34, 184, 207, .3)",
            borderColor: "transparent",
            pointBackgroundColor: "rgba(34, 184, 207, 1)",
            pointBorderColor: "#fff",
            pointHoverBackgroundColor: "#fff",
            pointHoverBorderColor: "rgba(34, 184, 207, 1)",
            data: [175, 120, 169, 82, 135, 169, 132, 130, 192, 230, 215, 260],
          },
          {
            label: "Last Year",
            fill: true,
            backgroundColor: "rgba(233, 236, 239, 1)",
            borderColor: "transparent",
            pointBackgroundColor: "rgba(233, 236, 239, 1)",
            pointBorderColor: "#fff",
            pointHoverBackgroundColor: "#fff",
            pointHoverBorderColor: "rgba(233, 236, 239, 1)",
            data: [220, 170, 110, 215, 168, 227, 154, 135, 210, 240, 145, 178],
          },
          {
            label: "Last Year2",
            fill: true,
            backgroundColor: "rgba(233, 236, 239, 1)",
            borderColor: "transparent",
            pointBackgroundColor: "rgba(233, 236, 239, 1)",
            pointBorderColor: "#fff",
            pointHoverBackgroundColor: "#fff",
            pointHoverBorderColor: "rgba(233, 236, 239, 1)",
            data: [22, 170, 110, 215, 168, 217, 154, 135, 210, 240, 145, 178],
          },
        ],
      },
    };
  },
  created() {
    // Set Chart.js configuration
    Chart.defaults.global.defaultFontColor = "#495057";
    Chart.defaults.global.defaultFontStyle = "600";
    Chart.defaults.scale.gridLines.color = "transparent";
    Chart.defaults.scale.gridLines.zeroLineColor = "transparent";
    Chart.defaults.scale.display = false;
    Chart.defaults.scale.ticks.beginAtZero = true;
    Chart.defaults.global.elements.line.borderWidth = 0;
    Chart.defaults.global.elements.point.radius = 0;
    Chart.defaults.global.elements.point.hoverRadius = 0;
    Chart.defaults.global.tooltips.cornerRadius = 3;
    Chart.defaults.global.legend.labels.boxWidth = 12;
  },
};
</script>
