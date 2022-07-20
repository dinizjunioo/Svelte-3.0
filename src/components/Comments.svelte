
<!--
<div class="container">
    <hr/>
        <div class="form-todo form-group">
            <p>
                <input placeholder="nome" type="text" name="author" class="input" v-model="name" />
            </p>
            <p>
                <input placeholder="comentario"  type="text" name="message" class="input2" v-model="message" >
            </p>
            <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
        </div>
  
        <div class="list-group">
            <div class="list-group-item" v-for="(comment, index) in allComments" v-bind:key="index">
                    <div class="autor">
                      Autor: {{comment.name}}
                    </div>
                    <div class="comment">
                      Comentárioaa: {{comment.message}}
                    </div>
                <div>
                    <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
                </div> 
            </div>
        </div> 
      <hr />
</div>

<script>
    export default {
      data() {
        return { 
          comments: [],
          name:'',
          message:''
        }
      },
      methods:{
        addComment(){
          if(this.message.trim() === ''){
            return;
          }
          this.comments.push({
            name: this.name,
            message: this.message
          });
          this.name='';
          this.message='';
    
        },
        removeComment(index){
          this.comments.splice(index,1);
        }
      },
      computed:{
        allComments(){
          return this.comments.map(comment => ({
            ...comment,
            name: comment.name.trim() === '' ? 'Anônimo' : comment.name
          }))
        }
      },
      watch:{
        comments (val){
          console.log('val',val)
        }
      }
    }
    
    </script>

   -->