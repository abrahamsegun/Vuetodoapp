<template >
    <div class="wrap">
        <div class="action">
            <form action=""  >

                <div class="inputcontainer">
                    <input class="inputFrom" type="text" v-model="Todo" @keyup.enter="HandleTodo"  
                   placeholder="Add a new todo"  />

                </div>
                <button class="inputFrombtn" @click="HandleTodo">Add Task</button>
            </form>
        </div>
        <div class="ull">
            <ul>
                <li v-for="(item, index) in setTodo" :key="index" > 
                     <input class="checkme" type="checkbox" v-model="item.isCompleted" @click="toggleinput"> 
                     <span class="text">{{ item.task}}</span>
      <button class="remove" @click="remove">Remove</button> 
    <button class="edit" @click="handleEdit" @keyup="handleEdit">Edit</button>
             </li>

            </ul>


        </div>
    </div>
</template>


<script setup>



import { ref, onMounted} from "vue";


const Todo = ref("");
const setTodo = ref([])

 const HandleTodo=(e)=>{
    e.preventDefault();
    if (Todo.value.trim() == ""){
        return
    }

    if(Todo.value.trim() !== ""){
     setTodo.value.push({task: Todo.value, isCompleted:false});
     saveTasks();
     Todo.value=""
    
     
    }

 }


 onMounted(() => {
    loadTasks();
 })

 const loadTasks=()=> {
      // Load tasks from local storage
      const stored = localStorage.getItem('setTodo');
      setTodo.value = stored ? JSON.parse(stored) : [];
    }

const  remove= (index)=> {
      setTodo.value.splice(index, 1);
      saveTasks();
    }
  const saveTasks=()=> {

      localStorage.setItem(' setTodo ', JSON.stringify(setTodo.value));
    }


const  handleEdit= (e)=> {
      let existingTodo = e.target.previousElementSibling.previousElementSibling.textContent;
    let newTodo = prompt('Enter new todo', existingTodo);
        // update li textContent
        if (newTodo===null) {
          newTodo= e.target.previousElementSibling.previousElementSibling.textContent
        }
        e.target.previousElementSibling.previousElementSibling.textContent = newTodo;

    }

const toggleinput=(event)=>{

    if (event.target.checked) {
    event.target.nextElementSibling.classList.add("completed")
  } else {
    event.target.nextElementSibling.classList.remove("completed")
    
  }
}


</script>
<style  scoped>
  .wrap{
    margin-top: 4rem;
    height: 30vh;
  }
    form{
        display: flex;
        flex-direction: row;
        width: 100%;
        margin: auto;
        justify-content: space-between;
        align-items: center;
    }
    .inputcontainer{
        width: 70%;
        
        overflow: visible;
    }     
.inputFrom{
    width: 100%;
    min-height: 3rem;
    border-radius: .2rem;
    font-size: 27px;
    box-sizing: border-box;
    background-color: rgb(165, 123, 123);
    color: black;
    padding: 0 .3rem;
    border: .3rem solid #ccc;
}

.inputFrombtn{
    width: 25%;
    height: 3rem;
    background-color: rgb(165, 123, 123);
    color: black;
    font-family: Poppins sans-serif;
    text-transform: capitalize;
    font-weight: 800;
    font-size: 24px;
    border: .2rem solid #ccc;
    border-radius: .5rem;

}

/* done and strike through */
.completed{
    text-decoration: line-through;
}
.ull{
  display: flex;
  flex-direction: column;
  list-style: none;
    margin: 2rem auto 0;
    padding: .5rem 0 ;

}
ul{
    list-style-type: none; 
    padding-inline-start: 0 ;
    width: 90%;
    margin:0 auto;
    border: .2rem solid  rgb(165, 123, 123);
    padding: 1rem;
    min-height: 10rem;
  
}
li{
    list-style: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: #5c3c92  .2rem solid;
    margin-top: .7rem;
    color: black ;


}
.checkme{
    width: 5%;
    height: 1.3rem;
}
.text{
    width: 70%;
}
.remove{
    width: 10%;
    
}
.edit{
    width: 10%;
}
    
    @media only screen and (max-width: 600px) {
      /* phone  */
      .wrap{
    margin-top: 1.8rem;
  }
  form{
        display: flex;
        flex-direction: row;
        width: 100%;
        margin: auto;
        justify-content: space-between;
        align-items: center;
    }
    .inputcontainer{
        width: 70%;
        
        overflow: visible;
    }     
.inputFrom{
    width: 100%;
    min-height: 3rem;
    border-radius: .2rem;
    font-size: 24px;
    box-sizing: border-box;
    background-color: rgb(165, 123, 123);
    color: black;
    padding: 0 .3rem;
    border: .2rem solid #ccc;
    border-radius: .5rem;
}

.inputFrombtn{
    width: 25%;
    height: 3rem;
    background-color: rgb(165, 123, 123);
    color: black;
    font-family: Poppins sans-serif;
    text-transform: capitalize;
    font-weight: 800;
    font-size: 16px;
    border: .2rem solid #ccc;
    border-radius: .5rem;

}
.ull{
  display: flex;
  flex-direction: column;
  list-style: none;
    margin: 2rem auto 0;
    padding: .5rem 0 ;

}
ul{
    list-style-type: none; 
    padding-inline-start: 0 ;
    width: 90%;
    margin:0 auto;
    border: .2rem solid  rgb(165, 123, 123);
    padding: 1rem;
  
}
li{
    list-style: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: #5c3c92  .2rem solid;
    margin-top: .7rem;
    color: black ;


}
.checkme{
    width: 5%;
    height: 1.3rem;
}
.text{
    width: 55%;
}
.remove{
    width: 20%;
    
}
.edit{
    width: 20%;
}
    }

    @media only screen and (min-width: 600px) {
        /* bigger phone and small tab */
     
        .wrap{
    margin-top: 2rem;
  }
  form{
        display: flex;
        flex-direction: row;
        width: 100%;
        margin: auto;
        justify-content: space-between;
        align-items: center;
    }
    .inputcontainer{
        width: 70%;
        
        overflow: visible;
    }     
.inputFrom{
    width: 100%;
    min-height: 3rem;
    border-radius: .2rem;
    font-size: 24px;
    box-sizing: border-box;
    background-color: rgb(165, 123, 123);
    color: black;
    padding: 0 .3rem;
    border: .2rem solid #ccc;
    border-radius: .5rem;
}

.inputFrombtn{
    width: 25%;
    height: 3rem;
    background-color: rgb(165, 123, 123);
    color: black;
    font-family: Poppins sans-serif;
    text-transform: capitalize;
    font-weight: 800;
    font-size: 18px;
    border: .2rem solid #ccc;
    border-radius: .5rem;
}
.ull{
  display: flex;
  flex-direction: column;
  list-style: none;
    margin: 2rem auto 0;
    padding: .5rem 0 ;

}
ul{
    list-style-type: none; 
    padding-inline-start: 0 ;
    width: 90%;
    margin:0 auto;
    border: .2rem solid  rgb(165, 123, 123);
    padding: 1rem;
  
}
li{
    list-style: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: #5c3c92  .2rem solid;
    margin-top: .7rem;
    color: black ;


}
   
    }

    @media only screen and (min-width: 768px) {
        /* tablet */
   
        .wrap{
    margin-top: 3.5rem;
  }
  form{
        display: flex;
        flex-direction: row;
        width: 100%;
        margin: auto;
        justify-content: space-between;
        align-items: center;
    }
    .inputcontainer{
        width: 70%;
        
        overflow: visible;
    }     
.inputFrom{
    width: 100%;
    min-height: 3rem;
    border-radius: .2rem;
    font-size: 24px;
    box-sizing: border-box;
    background-color: rgb(165, 123, 123);
    color: black;
    padding: 0 .3rem;
    border: .2rem solid #ccc;
    border-radius: .5rem;
}

.inputFrombtn{
    width: 25%;
    height: 3rem;
    background-color: rgb(165, 123, 123);
    color: black;
    font-family: Poppins sans-serif;
    text-transform: capitalize;
    font-weight: 800;
    font-size: 20px;
    border: .2rem solid #ccc;
    border-radius: .5rem;

}
.ull{
  display: flex;
  flex-direction: column;
  list-style: none;
    margin: 2rem auto 0;
    padding: .5rem 0 ;

}
ul{
    list-style-type: none; 
    padding-inline-start: 0 ;
    width: 90%;
    margin:0 auto;
    border: .2rem solid  rgb(165, 123, 123);
    padding: 1rem;
  
}
li{
    list-style: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: #5c3c92  .2rem solid;
    margin-top: .7rem;
    color: black ;


}

.checkme{
    width: 5%;
    height: 1.3rem;
}
.text{
    width: 70%;
}
.remove{
    width: 10%;
    
}
.edit{
    width: 10%;
}

    }
</style>




<!-- removeTodo(index) {
    this.todos.splice(index, 1);
  }, -->