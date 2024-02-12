<script>
    let src = '/img/basadur.png';    
</script>

<main>
    <section>
        <div class="Basadur">
            <h1>Perfil Basadur</h1>
            <p>para conocer tu perfil innovador <br> y tu funcion en el equipo</p>
        </div>
        <img {src} alt="basadur-foto">
    </section>
    
    <section>
        <div class="Personalidad">
            <h1>Perfil de Personalidad</h1>
            <p>para mejorar la empatía y <br> la comunicación hacia los demás</p>
        </div>
        <img src="/img/personalidad.png" alt="personalidad-foto">
    </section>
   
</main>

<style>
    main{
        padding: 20px;
    }
    section{
        display: flex;
        justify-content: space-around;
        margin-top: 10px;
    }

    .Basadur{
        margin-right: 98px;
    }

    h1{
        font-family: sansation;
        font-size: xx-large;
        font-weight: bold;   
    }

    p{
        font-family: sansation;
        font-weight: 100;
    }

    img{
        width: 19%;
    }

</style>