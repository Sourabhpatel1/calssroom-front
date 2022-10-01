<div class="banner">
    <div class="header">
        <h1>Welcome to Classroom</h1>
    </div>
    <div class="detail">
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Amet quos doloremque corrupti quas ipsum? Harum nostrum tempore eius fugiat mollitia!</p><br>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Necessitatibus dolore fuga id, doloremque voluptates dolor?</p><br>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Fugiat beatae perferendis quam quod perspiciatis aspernatur.</p><br>
    </div>
</div>

<style>
    .banner {
        font-size: 20px;
        min-height: 65vh;
        max-height: 70vh;
        max-width: 90%;
        margin: 0 auto;
        background: url('/images/banner.svg');
        object-fit: contain;
        background-size: cover;
        background-repeat: no-repeat;
        margin: 2rem 5rem;
        padding: 2rem;
        border-right: 2px solid rgb(255, 255, 255);
        border-bottom: 2px solid rgb(255, 255, 255);
        box-shadow: 2px 3px 5px 3px rgba(0, 0, 0, 0.144);
    }
    .header {
        font-size: 24px;
        width: 50vw;
        padding: 0.5rem 0;
        margin: 2rem 0;
        border-bottom: 1px solid rgb(0, 0, 0);
    }
    .header h1 {
        text-align: center;
    }
    .detail {
        width: 50vw;
        margin: 2rem 0;
    }
    .detail p {
        text-align: justify;
    }
    @media (max-width:500px) {
        .banner {
            font-size: 14px;
            margin: 0 auto;
            min-height: 100vh;
        }
    }
    @media (max-width:820px) {
        .banner {
            font-size: 12px;
            min-height: 40vh;
            max-height: 40vh;
        }
    }
    @media (max-width:1094px) {
        .header {
            font-size: 18px;
            width: 100%;
        }
        .detail {
            width: 100%;
        }
        .banner {
            font-size: 16px;
            max-height: 80vh;
            background: url('/images/banner-mobile.svg');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
    }
</style>