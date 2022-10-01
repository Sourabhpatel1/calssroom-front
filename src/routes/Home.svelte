<script>
    const handleClick = async ()=>{
        const res = await fetch('http://127.0.0.1:8000/token/refresh', {
            method: 'POST'
        })
        const data = await res.json()
        console.log(data)
    }
</script>
<h1>Home Page</h1>

<button on:click={handleClick}>fetch</button>