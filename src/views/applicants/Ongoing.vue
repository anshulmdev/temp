<template>
  <div>
    <!-- Hero -->
    <base-page-heading title="Applications Received" subtitle="Only invited candidates can apply in assignments">
      <template #extra>
        <b-breadcrumb class="breadcrumb-alt">
          <b-breadcrumb-item href="javascript:void(0)">Applicants</b-breadcrumb-item>
          <b-breadcrumb-item active>Applied</b-breadcrumb-item>
        </b-breadcrumb>
      </template>
    </base-page-heading>
    <!-- END Hero -->

    <!-- Page Content -->
    <div class="content">
      <!-- Full Table -->
      <base-block rounded title="Assignment: JavaScript">
        <template #options>
          <button type="button" class="btn-block-option">
            <i class="si si-settings"></i>
          </button>
        </template>
        <b-table-simple responsive bordered striped table-class="table-vcenter">
          <b-thead>
            <b-tr>
              <b-th class="text-center" style="width: 10%;">
                Resume
              </b-th>
              <b-th style="width: 20%;">Name</b-th>
              <b-th style="width: 20%;">Email</b-th>
              <b-th style="width: 30%;">Tags</b-th>
              <b-th style="width: 15%;">Experience</b-th>
            </b-tr>
          </b-thead>
          <b-tbody>
            <b-tr v-for="user in users" :key="user.id">
              <b-td class="text-center">
                <a v-b-modal.modal-block-extra-large>
                <img height="50" :src="user.avatar" alt="Avatar"></a>
              </b-td>
              <b-td class="font-w600 font-size-sm">
                <a :href="`${user.href}`">
                  {{ user.name }}
                </a>
              </b-td>
              <b-td class="font-size-sm">
                client{{ user.id }}<em class="text-muted">@example.com</em>
              </b-td>
              <b-td>
                <b-row v-for="(value,index) in user.labelVariant" :key="index">
                  <b-col class="col-lg-4">
                <b-badge :variant="index">{{ value }}</b-badge></b-col>
                </b-row>
              </b-td>
              <b-td class="font-size-sm">
                {{ user.exp }} Yrs
              </b-td>
            </b-tr>
          </b-tbody>
        </b-table-simple>
          <b-pagination v-model="currentPage" :total-rows="rows" :per-page="perPage" size="sm"></b-pagination>
      </base-block>
      
          <!-- Extra Large Block Modal -->
          <b-modal id="modal-block-extra-large" size="xl" body-class="p-0" hide-footer hide-header>
            <div class="block block-rounded block-themed block-transparent mb-0">
              <div class="block-header bg-primary-dark">
                <h3 class="block-title">Modal Title</h3>
                <div class="block-options">
                  <button type="button" class="btn-block-option" @click="$bvModal.hide('modal-block-extra-large')">
                    <i class="fa fa-fw fa-times"></i>
                  </button>
                </div>
              </div>
              <div class="block-content font-size-sm">
                ss
              </div>
              <div class="block-content block-content-full text-right border-top">
                <b-button variant="alt-primary" class="mr-1" @click="$bvModal.hide('modal-block-extra-large')">Close</b-button>
                <b-button variant="primary" @click="$bvModal.hide('modal-block-extra-large')">Ok</b-button>
              </div>
            </div>
          </b-modal>
          <!-- END Extra Large Block Modal -->
      <!-- END Full Table -->
    </div>
    <!-- END Page Content -->
  </div>
</template>

<script>
export default {
  components: {
  },
  data () {
    return {
      users: [
        {
          id: 0,
          name: 'Adam McCoy',
          avatar: 'https://cdn.iconscout.com/icon/free/png-256/resume-1956282-1650445.png',
          href: 'javascript:void(0)',
          labelVariant: {'warning':'javascript'},
          exp:10,
        },
        {
          id: 1,
          name: 'Neo McCoy',
          avatar: 'https://cdn.iconscout.com/icon/free/png-256/resume-1956282-1650445.png',
          href: 'javascript:void(0)',
          labelVariant: {'info':'React'},
          exp:10,
        },
        {
          id: 2,
          name: 'Eve McCoy',
          avatar: 'https://cdn.iconscout.com/icon/free/png-256/resume-1956282-1650445.png',
          href: 'javascript:void(0)',
          labelVariant: {'success': 'vuejs'},
          exp:10,
        },
        {
          id: 3,
          name: 'Adam McCoy',
          avatar: 'https://static.thenounproject.com/png/543772-200.png',
          href: 'javascript:void(0)',
          labelVariant: {'warning':'javascript'},
          exp:10,
        },
        {
          id: 4,
          name: 'Adam McCoy',
          avatar: 'https://static.thenounproject.com/png/543772-200.png',
          href: 'javascript:void(0)',
          labelVariant: {'danger': 'angular'},
          exp:10,
        },
      ]
    }
  }
}
</script>
