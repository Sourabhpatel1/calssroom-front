<script>
    export let name;
    export let description;
    export let price;
</script>

<div class="card">
    <div class="card-title">
        <h2>{name}</h2>
    </div>
    <hr>
    <div class="card-description">
        <blockquote>{description}</blockquote>
    </div>
    <hr>
    <div class="price"><p class="price-text">Price: ₹{price}</div>
    <a href="/" class="action">Enroll Now</a>
</div>

<style>
    .card {
        text-align: justify;
        font-size: 20px;
        height: 450px;
        width: 450px;
        min-width: 250px;
        padding: 1.5rem;
        border-radius: 16px;
        background: rgb(255, 255, 255);
        box-shadow: 1rem 0 3rem rgba(8, 8, 8, 0.212);
        display: flex;
        flex-direction: column;
        gap: 1rem;
        transition: 0.2s;
        margin: 0;
        scroll-snap-align: start;
        clear: both;
        position: relative;
    }
    .card:hover {
        transform: translateY(-1.5rem);
        box-shadow: 1.5rem 0 3.5rem rgba(8,8,8,0.400);
    }
    .action {
        position: relative;
        text-decoration: none;
        color: black;
        margin-top: 1.5rem;
        padding: 0.5rem 0 0.5rem 0;
        border: solid 1px black;
        width: 30%;
        text-align: center;
        transition: 0.3s ease-in-out;
    }

    .action:hover {
        background: rgba(157, 255, 0, 0.692);
        color: rgb(0, 0, 0);
    }

    @media (max-width:512px) {
        .card {
            max-width: 300px;
            font-size: 18px;
        }
        .action {
            width: 50%;
        }
    }
</style>
