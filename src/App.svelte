<!--<Quiz />-->


<script>
import { createEventDispatcher } from 'svelte';

import './assets/base.css';
//import Quiz from './components/quiz.svelte';
//import Comments from './components/Comments';

import TabNav from './components/TabNav.svelte';

import Tab from './components/Tab.svelte';

 let tabs = ['Comentários', 'Home'];
 let activeTab = 'Comentários';

 const tabChange = (e) =>
 {
    activeTab = e.detail;
 }
 let newComments = [
    {
        id: 1,
        author:'',
        comentario:''
    }
 ];

const handleAdd = (e) =>
{
    const Comm = e.detail;
    newComments = [Comm, ...newComments]
}
</script>

<div id="app">
    
    <h1>Vamos lá</h1>
     <Tab {activeTab}{tabs} on:tabChange={tabChange}/>
     {#if activeTab === 'Comentários'}
        <div>
           <TabNav on:add={handleAdd} {newComments}/>
        </div>
        
    {/if}
</div>

<style>
    .app
    {
        background-color: #444;
    }

</style>


