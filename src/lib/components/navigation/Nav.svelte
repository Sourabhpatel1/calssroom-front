<script>
  import Router from 'svelte-spa-router';
  import {push, pop, replace} from 'svelte-spa-router'
  import {location} from 'svelte-spa-router'
  import { onMount } from 'svelte';
  import About from '../../../routes/About.svelte';
  import Error from '../../../routes/Error.svelte';
  import Home from '../../../routes/Home.svelte';
  import Login from '../../../routes/Login.svelte';
  import Register from '../../../routes/Register.svelte';
  import {authenticated} from '../../store.js'

  $:current = $location

  let routes = {
    "/": Home,
    "/about": About,
    "/register": Register,
    "/login": Login,
    "*": Error
  }

  let active = false

  const toggleMenu = ()=>{
    active = !active
  }

  onMount(async ()=>{
    if (!$authenticated) {
        const res = await fetch('http://127.0.0.1:8000/token/refresh', {
            method:'POST'
        })
        if (res.status !== 400) {
            $authenticated = true
        }
    }
    console.log($authenticated)
  })

</script>

<div>
    <nav class="navbar">
        <div class="left">
            <div class="logo">
                <a href="#/"><h2><strong>Classroom</strong></h2></a>
            </div>
            <div class="page-actions menu">
                <a href="#/" class:is-active='{current === '/'}'>Home</a>
                <a href="#/about" class:is-active='{current === '/about'}'>About</a>
            </div>
        </div>
        <div class="user-actions menu right">
            {#if $authenticated===false}
            <a href="#/register" class:is-active='{current === '/register'}'>Register</a>
            <a href="#/login" class:is-active='{current === '/login'}'>Login</a>
            {:else}
                <a href="#/logout">Logout</a>
            {/if}
        </div>
        <div class="hamburger" class:active on:click={toggleMenu}>
            <span class="line"></span>
            <span class="line"></span>
            <span class="line"></span>
        </div>
    </nav>
</div>

<div class:active class="mobile-nav">
    <div class="mobile-menu">
        <a href="#/" on:click={toggleMenu}>Home</a>
        <a href="#/about" on:click={toggleMenu}>About</a>
        <a href="#/register" on:click={toggleMenu}>Register</a>
        <a href="#/login" on:click={toggleMenu}>Login</a>
        <a href="#/logout" on:click={toggleMenu}>Logout</a>
    </div>
</div>

<Router {routes}/>

<style>
    .mobile-nav {
        position: fixed;
        background: white;
        left: 150%;
        opacity: 0;
        width: 100%;
        height: 100vh;
        display: block;
        transition: 600ms ease-in-out all;
    }

    .mobile-menu {
        position: absolute;
        top: 100px;
        margin-top: 1rem;
        margin-bottom: 1rem;
        height: 100%;
        width: 100%;
        gap: 2rem;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
    }

    .mobile-menu a {
        font-weight: 600;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        width: 50%;
        height: 4.5rem;
        padding: 2px 5px;
        background-color: rgba(150, 240, 6, 0.281);
        border-radius: 5px;
        color: black;
        transition: 450ms ease-in-out;
    }

    .mobile-menu a:hover {
        background-color: rgba(220, 20, 60, 0.432);
        color: white;
    }

    .menu {
        display: none;
    }

    a {
        text-decoration: none;
        margin: 0 0 0 0.8rem;
        padding: 0.3rem 1rem;
        color: black;
    }

    .user-actions
    a:hover {
        /* color: rgb(0, 119, 255); */
        background: rgba(150, 240, 6, 0.281);
        border-radius: 15px;
    }

    .page-actions
    a:hover {
        /* color: rgb(0, 119, 255); */
        background: rgba(150, 240, 6, 0.281);
        border-radius: 15px;
    }

    .logo > a > h2 {
        padding: 5px;
        border: 4px solid black;
    }

    .logo > a :hover {
        color: rgba(150, 240, 6, 1);
    }

    .navbar {
        z-index: 999;
        position: fixed;
        width: 100vw;
        height: 100px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        background: rgb(250, 249, 249);
        box-shadow: 2px 3px 5px rgba(0,0,0,0.5);
    }

    .left {
        display: flex;
        align-items: center;
        gap: 5rem;
        margin-left: 3rem;
    }

    .right {
        margin-right: 3rem;
    }

    .hamburger {
        margin-right: 3rem;
        outline: none;
        border: none;
        background: none;
        display: flex;
        flex-direction: column;
        gap: 0.3rem;
        cursor: pointer;
    }
    
    .line {
        height: 3px;
        width: 30px;
        background-color: black;
        transition: 300ms ease-in-out all;
    }

    .hamburger:hover .line {
        background-color: rgb(120, 185, 14);
    }

    .hamburger:hover span:nth-child(2) {
        transform: translateX(10px);
    }

    .hamburger.active span {
        background-color: rgb(220, 20, 60);
    }

    .hamburger.active span:nth-child(2) {
        display: none;
    }

    .hamburger.active span:nth-child(1) {
        transform: translate(0px, 4px) rotate(45deg);
    }    

    .hamburger.active span:nth-child(3) {
        transform: translate(0px, -3px) rotate(-45deg);
    }

    .mobile-nav.active {
        opacity: 1;
        left: 0%;
    }

    .mobile-nav.active :global(body) {
        overflow-y: hidden;
    }

    .mobile-nav.active :global(*) {
        overflow: hidden;
    }

    .is-active {
        border: solid 2px rgba(150, 240, 6, 1);
        border-radius: 15px;
    }

    @media (min-width:1028px) {
        .mobile-nav {
            display: none;
        }
        .hamburger {
            display: none;
        }
        .menu {
            display: block;
        }
        @media (max-width:1300px) {
            * {
                font-size: 18px;
            }
        }
    }
</style>