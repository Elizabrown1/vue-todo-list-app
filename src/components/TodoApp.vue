<template>
<section class="vh-500 gradient-custom-2 box" style=" ">
  <div class="container py-5 h-100 ">
    <div class="row d-flex justify-content-center align-items-center   h-100"  >
      <div class="col-md-12 col-xl-8 " >
        <div class="card p-5 top 
         gradient-custom-2"  >
          <div class="card-body p-4 text-white">
            <div class="text-center pt-2 pb-2 ">
              <img class="animate__animated animate__slower animate__zoomIn animate__infinite" src="https://mdbcdn.b-cdn.net/img/Photos/new-templates/bootstrap-todo-list/check1.webp" alt="Check" width="60">
    
                <h2 class="animate__animated animate__backInUp my-4">Task List</h2>


    <div class="d-flex justify-content-center align-items-center text-white mb-5 ">
      <input v-model="task" type="text" placeholder="Enter task" class="form-control " style="
       " />
      <button @click="submitTask" class="btn  but p-2 ">Submit</button>
    </div>

    <table class="table text-white mb-0">
  <thead>
    <tr class=""> 
      <th scope="col">Task To Do</th>
      <th scope="col">Status</th>
      <th scope="col" class="text-center">Edit</th>
      <th scope="col" class="text-center">Delete</th>
    </tr>
  </thead>
  <tbody>
    <tr class="fw-normal" v-for="(task,index) in tasks" :key="index">
      <td>
        <span :class="{'finished': task.status === 'finished'}">{{task.name}}</span>
      </td>
      <td style="width: 120px; font-size: 20px">
        <span @click="changeStatus(index)" class="pointer"
        :class="{'text-danger':task.status === 'to-do',
        'text-warning':task.status === 'in-progress',
        'text-success':task.status === 'finished',
        
        }"
        >
          {{firstCharUpper(task.status)}}
        </span>
      </td>
      <td>
        <div class="text-center" @click="editTask(index)">
          <span class="fa fa-pen text-info"></span>
        </div>
      </td>
      <td>
        <div class="text-center" style="color: white;" @click="deleteTask(index)">
          <span class="fa fa-trash"></span>
        </div>
      </td>
    </tr>
    
  </tbody>
</table>
            </div>
          </div>
          </div>
      </div>
    </div>
  </div>
</section>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      task:'',
      editedTask: null,
      availableStatuses: ['to-do', 'in-progress', 'finished'],
      tasks: [
        {
          name:'Get some bananas from the store.',
          status:'to-do'
        },
         {
          name:'Go to the mall in 2 hours.',
          status:'in-progress'
        }
      ]
    }
  },

  methods: {
    submitTask(){
      if(this.task.length === 0) return;

      if(this.editedTask === null){
      this.tasks.push({
        name :this.task,
        status: 'to-do'
      });
      }else{
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null
      }
      this.task = '';
    },

    deleteTask(index){
      this.tasks.splice(index, 1);
    },
    editTask(index){
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },
    changeStatus(index){
      let newIndex = this.availableStatuses.indexOf(this.tasks[index].status);
      if(++newIndex > 2) newIndex = 0;
      this.tasks[index].status = this.availableStatuses[newIndex];
    },
    firstCharUpper(str){
      return str.charAt(0).toUpperCase() + str.slice(1);
    }
  }
}
</script>

  
<style scoped>
.pointer{
  cursor: pointer;
}
.finished{
  text-decoration: line-through;
}
          .form-control{

                width: 40%;
                justify-content: center;
              
                
                
            }
           .form-control:hover{
             width: 100%;
             transition: 1s;
               /* border-radius: solid rgb(66, 243, 101) 3px; */
               box-shadow: 20px, 20px, 20px black;

           }

            .but{

              background-color: white;  width: 120px; margin-left: 10px;
               color: black; 
               width: 100px;
               height: 38px;
                
            }
           .but:hover{
             transition: 0.5s;
             background-color:#0DCAF0 ;
             color: white;
             box-shadow: 20px, 20px, 20px black !important; 
              border-radius: solid black 5px !important;
             
           }

           .top{
             background-color: #368fbf;
             
             box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px, rgba(10, 37, 64, 0.35) 0px -2px 6px 0px inset;
             /* --box-reflect: below 0px linear-gradient(transparent, transparent, #004); */
           } 
           .box{
             background-color: #84c8e1 ;
           }
        
</style>