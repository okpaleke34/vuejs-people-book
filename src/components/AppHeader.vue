<template>
    <header class="header"> 
        <h1 class="title"> People Book</h1>
        <ul>
            <li>
                <router-link to="/">Home</router-link> 
            </li> 
            <li>
                <router-link to="/saved">Saved People</router-link>
            </li> 
            <li>
                <router-link to="/about">About</router-link>
            </li>    
        </ul>
    </header>
  <router-view/>
  
</template>

<script>

export default {
    name:'AppHeader'
}
</script>

<style>
    .header{
        display:flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 1rem;
        padding-bottom: 1rem;
        border-bottom:1px dotted #ccc;
    }
    .header .title{
        font-size:3rem;
        color: #526488
    }
    .header ul{
        display: flex;
        list-style-type: none;
    }
    .header a{
        display: inline-block;
        background: #333;
        color:#fff;
        padding:0.3rem 1rem;
        text-decoration: none;
        margin-right:0.5rem
    }
    table{
    width: 100%;
    border-collapse: collapse;
    text-align: left;
    overflow: hidden;
    
        }
    td, th{
        border-top: 1px solid #ECF0F1;
        padding: 10px;
    }
    
    td{
        border-left: 1px solid #ECF0F1;
        border-right: 1px solid #ECF0F1;
    }
    
    th{
        background-color: #4ECDC4;
    }
    
    tr:nth-of-type(even) td{
        background-color: lighten(#4ECDC4, 35%);
    }
</style>
