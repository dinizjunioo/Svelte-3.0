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

    if ((comments.author.trim().length > 5) && (comments.comentario.trim().length > 5))
    {
        valid = true;
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
        <button>Salvar</button>
    </div>
    
    <div class="comment-list">
        {#each newComments as comment (comment.id)}
            <div>
                {comment.author}
                {comment.comentario}
            </div>
        {/each}
    </div>
</form>

<style>
form{
    text-align: center;
    
    margin-bottom: 10px;
    color:brown;
    
}
</style>