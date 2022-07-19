<script>
    import {createEventDispatcher} from 'svelte';
    const dispatch = createEventDispatcher();
    export let tabs;
    export let activeTab;
</script>

<div class="tab">
    <ul>
        {#each tabs as tab}
        <li on:click={() => dispatch('tabChange', tab)}>
            <div class:active={tab === activeTab}>
                {tab}
            </div>
         </li>   
        {/each}
    </ul>
</div>
<!--v-on:click="addComment"-->
<style>
.tab{
    margin-bottom: 40px;
   
}
ul{
 
    display:flex;
    justify-content: center;
    padding: 0;
    list-style-type: none;
    cursor: pointer;
    
}
li{
    margin: 0 16px;
    font-size: 18px;
}
.active{
    color:rgb(62, 8, 73);
    border-bottom: 2px solid rgb(182, 174, 65);
    padding-bottom: 10px;
}
</style>