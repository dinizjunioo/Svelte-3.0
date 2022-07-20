<script>
    import {createEventDispatcher} from 'svelte';
    const dispatch = createEventDispatcher();
    
    export let newComments = [];

    let comments = {      
        id: 1,
        author:'',
        comentario:''
    }
    const submitHandler = () =>
    {
    
    var valid = false;

    if ((comments.author.trim().length > 0) && (comments.comentario.trim().length >= 5))
    {
        valid = true;
    }else{
        if(comments.author.trim().length == 0)
        {
            alert("Digite seu nome!");
        }else if(comments.comentario.trim().length < 5){
            alert("O comentário precisa ter no mínimo 5 caracteres.");
        }else{
            alert("Ao menos um campo está vazio. Digite seu nome e seu comentário.");
        }
    }

    if (valid)
    {

        let poll = 
        {
            ...comments,
            id: Math.random()
       }
      
        dispatch('add', poll);
        console.log('valid', comments);
        console.log(poll);
    }
    }
    
    
</script>

<form on:submit|preventDefault={submitHandler}>
    <div>
        <label for="author">Author:</label>
        <input type="text" class="input" bind:value={comments.author}>
    </div>
    <div>
        <label for="comentario">Comentário:</label>
        <input type="text" class="input" bind:value={comments.comentario}>
    </div>
    <div>
        <button class="button-1">Salvar</button>
    </div>
    
    <div class="comment-list">
        {#each newComments as comment (comment.id)}    
            {#if comment.id != 1}        
            <div class="principal">
                <div class="autor">
                   Autor: {comment.author}
                </div>
                <div class="comentario">
                    Comentário: {comment.comentario}
                </div>
            </div>
            {/if}
        {/each}
    </div>
</form>

<style>
form{
    align-items: center;
  text-align: center;
    
    margin-bottom: 10px;
    color:brown;
    
}
.principal
{
    align-items: center;
  text-align: center;
}
.autor
{
    margin-bottom: 40px;
  border-radius: 5px;
  height: 40px;
  width: 300px;
  padding: 0px 10px 0px 10px;
  border: none;
  margin-bottom: 10px;
  background-color: rgb(12, 41, 31);
  color:rgb(181, 205, 226);

  align-items: center;
  text-align: center;
}

.comentario
{
    margin-bottom: 40px;
  border-radius: 5px;
  height: 40px;
  width: 300px;
  padding: 0px 10px 0px 10px;
  border: none;
  margin-bottom: 10px;
  background-color: rgb(12, 41, 31);
  color:rgb(181, 205, 226);

  align-items: center;
  text-align: center;
}
     /* CSS */
.input
     {
        height: 40px;
    width: 300px;
    padding: 0px 10px 0px 10px;
    border-radius: 5px;
    border: none;
    margin-bottom: 10px;
    background-color: rgb(12, 41, 31);
    color:rgb(181, 205, 226);
     }
.button-1{
    margin-top: 30px;
  background-color: #2c73c5;
  border-radius: 8px;
  border-style: none;
  box-sizing: border-box;
  color: #FFFFFF;
  cursor: pointer;
  display: inline-block;
  font-family: "Haas Grot Text R Web", "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 14px;
  font-weight: 500;
  height: 40px;
  line-height: 20px;
  list-style: none;
  margin: 0;
  outline: none;
  padding: 10px 16px;
  position: relative;
  text-align: center;
  text-decoration: none;
  transition: color 100ms;
  vertical-align: baseline;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.button-1:hover,
.button-1:focus {
  background-color: #F082AC;
}
</style>