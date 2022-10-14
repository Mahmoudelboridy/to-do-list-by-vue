<template>
<div id="dd" >
    <h1 style="margin-left:24px" >Vue Todo List</h1>
    <div class="add-task">
        <input type="text" v-model="task"   />
        <button style="margin-left:5px" v-on:click="addtask()">add task</button>
        <table id="tbody">
            <tr v-for="(task,index) in tasks">
                <td id="d1">{{task}}</td>
                <td id="d2"><button v-on:click="remove(index)" style="margin-left:5px;border:none">x</button></td>
            </tr>
        </table>
        <button v-on:click="removeall()" style="margin-top:15px">delete all</button>
    </div>
</div>
</template>
<script>

export default{
    data(){
        return{
            tasks:['read book','stydy','go to aunt'],
            task:' '
        }
    },
    created () {
       this.tasks=JSON.parse(localStorage.nfo);

    },
    methods:{
        remove(i){
            this.tasks.splice(i,1);
            localStorage.setItem("nfo", JSON.stringify(this.tasks));

        },

        removeall(){
                        this.tasks.splice(0,this.tasks.length);
                        localStorage.setItem("nfo", JSON.stringify(this.tasks));



                      },
                      addtask(){
                if(this.task != ' '){
                this.tasks.push(this.task)  ;
                }
                localStorage.setItem("nfo", JSON.stringify(this.tasks));
                 this.task=' ';
            },
            
       
    }
}
</script>
<style >
table{
margin-top:15px;
}
#d1{
    width: 165px;
}
#dd{
    margin-left: -100px;
    border: 2px hidden ;
    width: 300px;
    height: auto;
    background-color: #ffebcd;
    padding-left: 70px;
}
table{
    color: black;
    font-size: 15pt;
    font-weight: bold;
    font-family: Serif;
}
button{
    background-color: #cce0ff;
}

</style>