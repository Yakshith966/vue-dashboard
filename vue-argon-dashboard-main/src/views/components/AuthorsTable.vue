<template >
  <div class="card">
    <div class="card-header pb-0">
      <h6>Homepage</h6>
      <div>
        <div class="col-5 w-95 text-end mb-4">
          <argon-button color="dark" variant="gradient" @click="openModal">
            <i class="fas fa-plus me-2"></i>
            Add
          </argon-button>
        </div>

        <!-- Bootstrap Modal -->
        <div
          class="modal fade"
          id="myModal"
          tabindex="-1"
          role="dialog"
          aria-labelledby="exampleModalLabel"
          aria-hidden="true"
        >
          <div class="modal-dialog" role="document">
            <div class="modal-content">
              <!-- Your modal content goes here -->
              <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">Add Item</h5>
                <button
                  type="button"
                  class="close"
                  data-dismiss="modal"
                  aria-label="Close"
                >
                  <span aria-hidden="true">&times;</span>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div
      class="modal fade"
      id="myModal"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Add Item</h5>
            <button
              type="button"
              class="close"
              data-dismiss="modal"
              aria-label="Close"
            >
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <!-- Your form fields go here -->
            <form @submit.prevent="handleSubmit">
              <div class="mb-3">
                <label for="imageFile" class="form-label">Image File</label>
                <input type="file" class="form-control" id="imageFile" @change="handleFileChange">
              </div>
              <div class="mb-3">
                <label for="title" class="form-label">Title</label>
                <input
                  type="text"
                  class="form-control"
                  id="title"
                  v-model="formData.title"
                />
              </div>
              <div class="mb-3">
                <label for="content" class="form-label">Content</label>
                <textarea
                  class="form-control"
                  id="content"
                  rows="3"
                  v-model="formData.content"
                ></textarea>
              </div>
              <button type="submit" class="btn btn-primary">Submit</button>
            </form>
          </div>
        </div>
      </div>
    </div>

    <div class="card-body px-0 pt-0 pb-2">
      <div class="table-responsive p-0">
        <table class="table align-items-center mb-0">
          <thead>
            <tr>
              <th
                class="text-uppercase text-secondary text-xxs font-weight-bolder opacity-7"
              >
                Title
              </th>
              <th class="">Content</th>
              <th
                class="text-center text-uppercase text-secondary text-xxs font-weight-bolder opacity-7"
              >
                Edit
              </th>
              <th
                class="text-center text-uppercase text-secondary text-xxs font-weight-bolder opacity-7"
              >
                Delete
              </th>
              <th class="text-secondary opacity-7"></th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item, index) in items" :key="index">
              <td style="white-space: normal">
                <div class="d-flex px-2 py-1">
                  <div>
                    <img
                      src="../../assets/img/team-2.jpg"
                      class="avatar avatar-sm me-3"
                      alt="user1"
                    />
                  </div>
                  <div class="">
                    <h6 class="mb-0 text-sm">{{ item.title }}</h6>
                    <!-- <p class="text-xs text-secondary mb-0">{{ item.content }}</p> -->
                  </div>
                </div>
              </td>
              <td style="width: 550px">
                <p
                  class="text-xs font-weight-bold mb-0"
                  style="white-space: normal; overflow: hidden"
                >
                  {{ item.content }}
                </p>
                <!-- <p class="text-xs text-secondary mb-0">{{ item.organization }}</p> -->
              </td>
              <td>
                <div class="ms-auto text-end">
                  <a
                    class="btn btn-link text-dark px-3 mb-0"
                    href="javascript:;"
                  >
                    <i
                      class="fas fa-pencil-alt text-dark me-2"
                      aria-hidden="true"
                    ></i
                    >Edit
                  </a>
                </div>
              </td>
              <td>
                <div class="ms-auto text-end">
                  <a
                    class="btn btn-link text-danger text-gradient px-3 mb-0"
                    href="javascript:;"
                  >
                    <i class="far fa-trash-alt me-2" aria-hidden="true"></i
                    >Delete
                  </a>
                </div>
              </td>
              <!----- <td class="align-middle text-center text-sm">
                <span class="badge badge-sm" :class="{'bg-gradient-success': item.status === 'Online', 'bg-gradient-secondary': item.status === 'Offline'}">{{ item.status }}</span>
              </td>
              <td class="align-middle text-center">
                <span class="text-secondary text-xs font-weight-bold">{{ item.employed }}</span>
              </td>
              <td class="align-middle">
                <a href="javascript:;" class="text-secondary font-weight-bold text-xs" data-toggle="tooltip" data-original-title="Edit user">Edit</a>
              </td> -->
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ArgonButton from "@/components/ArgonButton.vue";



export default {
  components: {
    ArgonButton,
  },
  name: "authors-table",
  data() {
    return {
      formData: {
        imageFile: null,
        title: '',
        content: '',
      },
      items: [],
    };
  },
  mounted() {
    // Fetch data from your API
    this.fetchData();
  },
  methods: {
    
    
    async fetchData() {
      try {
        const response = await axios.get("http://localhost:8000/api/homepages");
        this.items = response.data.data;
      } catch (error) {
        console.error("Error fetching data:", error);
      }
    },
  },
};
</script>
