<script>
    let username;
    let password;

    const handleSubmit = async ()=>{
        const res = await fetch("https://classroom-production.up.railway.app/token/", {
            method:'POST',
            credentials:'include',
            mode:'cors',
            referrerPolicy: 'origin',
            headers : {
                "Access-Control-Allow-Origin": "http://localhost:5173/",
                "Content-Type" : "application/x-www-form-urlencoded"
            },
            body: `username=${username}&password=${password}`
        })
        const data = await res.json()
        console.log(data)
    }
</script>

<main>
    <div class="login-card">
        <form class="login-form" on:submit|preventDefault={handleSubmit}>
            <div class="login-prompt">
                <h3>Login Here</h3>
                <hr>
            </div>
            <div class="form-fields">
                <input type="email" placeholder="Enter Your Email" bind:value={username}/>
                <input type="password" placeholder="Enter Your Password" bind:value={password}/>
            </div>
            <div class="button">
                <button>Login</button>
            </div>
        </form>
    </div>
</main>

<style>
    main {
        padding: 1.5rem;
        margin: 0 auto;
        min-width: 100vw;
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .login-card {
        padding: 1.5rem;
        margin: 0 auto;
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        height: 600px;
        width: 800px;
        box-shadow: 0 0 30px rgba(0, 0, 0, 0.767);
        background-color: rgba(255, 255, 255, 0.459);
        border-radius: 25px;
    }
    .login-form {
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-evenly;
    }
    .login-prompt {
        width: 70%;
        text-align: center;
        padding: 10px;
    }
    .login-prompt h3 {
        width: 85%;
        margin: 0 auto;
        margin-bottom: 50px;
        border: solid black 3px;
        padding: 1rem;
    }
    .form-fields {
        min-width: 75%;
        padding: 1rem;
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }
    input{
        width: 90%;
        margin: 0 auto;
        text-align: center;
        padding: 20px;
        border: 1px solid rgba(0, 0, 0, 0.055);
        border-radius: 15px;
        transition: 0.4s ease-in-out;
    }
    input:focus {
        border: 1px solid rgb(255, 196, 0);
        background-color: rgba(150, 240, 6, 0.281);
    }
    .button {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    button {
        width: 200px;
        padding: 0.5rem;
        background: none;
        border: 1px solid rgb(255, 123, 0);
        background-color: rgba(136, 255, 0, 0.384);
        transition: 0.1s ease-in-out;
    }
    button:hover,
    button:focus {
        box-shadow: 0px 0 25px rgb(117, 187, 4);
        /* transform: scaleX(1.01); */
        background-color: rgb(136, 255, 0);
        cursor: pointer;
    }
</style>
