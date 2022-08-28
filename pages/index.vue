<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-lg-12 text-center">
          <h1 class="page-title"> PRODUCT PAGE</h1>
        </div>
        <div class="col-lg-12">
          <form action="#" method="post" enctype="multipart/form">
            <div class="row">
              <div class="col-lg-8">
                <h3 class="title">ADD NEW PRODUCTS</h3><br>
                <div class="form-group">
                  <label class="col-lg-6 control-label" for="product_name">PRODUCT NAME</label>
                  <div class="col-8">
                    <input name="name" class="form-control" required="" type="text">
                  </div>
                </div>
                <!-- File Button -->
                <div class="form-group">
                  <label class="col-lg-6 control-label" for="filebutton">IMAGE</label>
                  <div class="col-8">
                    <input name="image" class="input-file" type="file">
                  </div>
                </div>
                <div class="form-group">
                    <label class="col-lg-6 control-label" for="price">PRODUCT PRICE</label>
                    <div class="col-8">
                      <input name="price" class="form-control" required="" type="text">
                    </div>
                </div><br>
                <!-- Button -->
                <div class="form-group">
                  <div class="col-8">
                    <button id="submit" name="submit" class="btn btn-primary">ADD</button>
                  </div>
                </div>
              </div>
            </div>
          </form>
          <div class="col-lg-12 mt-5">
            <h3 class="title">PRODUCT DETAILS</h3>
            <table class="table table-striped">

              <thead>
                <tr>
                  <th scope="row">ID</th>
                  <th scope="col">NAME</th>
                  <th scope="col">IMAGE</th>
                  <th scope="col">PRICE</th>
                  <th scope="col">STATUS</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(task, index) in tasks" :key="index">
                  <td scope="row">{{ tasks.id }}</td>
                  <td>{{ tasks.name }}</td>
                  <td>{{ tasks.image }}</td>
                  <td>{{ tasks.price }}</td>
                  <td>
                    <span v-if="task.status == 0" class="badge bg-warning"> Inactive </span>
                    <span v-else class="badge bg-success"> Active </span>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>

    <div class="modal fade" id="staticBackdrop" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1" aria-labelledby="staticBackdropLabel" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="staticBackdropLabel">Modal title</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
              <h1>Edit Product</h1>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <button type="button" class="btn btn-primary">Done</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'home',
  layout: 'dashboard',
  data(){
    return{
      tasks:[],
    }
  },
  methods: {
    getTasks(){
      this.$axios.get('http://127.0.0.1:8000/api/tasks').then(response =>{
        this.tasks = response.data;
        console.log(response.data);
      });
    }
  },
  fetched() {
    this.getTasks();
  },
}
</script>
<style>
    .page-title{
        padding-top: 5vh;
        padding-bottom: 5vh;
        font-size: 3rem;
        color:rgb(0, 88, 175);
    }
    .form-group{
        color: rgb(166, 70, 70);
        font-size: 0.8rem;
        padding: 0.5vh;
    }
    .title{
        color: rgb(74, 142, 214);
        text-decoration: underline;
    }
</style>
