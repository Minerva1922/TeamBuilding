<main>
    <h1>Comencemos...</h1>
    <section>
        <div class="PerfilBasadur">
            <h2>Perfil <br> Basadur</h2>
            <p class="descripcion">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Obcaecati, distinctio alias culpa perspiciatis suscipit dolorum totam? Officiis expedita aspernatur nisi atque illum alias architecto natus, vel, autem corporis corrupti deserunt.</p>
            <button>Haz el test</button>
            <p class="detalles">Más detalles</p>
        </div>
        <div class="PerfilPersonalidad">
            <h2>Perfil de Personalidad</h2>
            <p class="descripcion">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Obcaecati, distinctio alias culpa perspiciatis suscipit dolorum totam? Officiis expedita aspernatur nisi atque illum alias architecto natus, vel, autem corporis corrupti deserunt.</p>
            <button>Haz el test</button>
            <p class="detalles">Más detalles</p>
        </div>
    </section>
</main>

<style>
    main{
        font-family: sansation;
    }

    h1{
        text-align: center;
    }

    h2{
        text-align: center;
        font-size: xxx-large;
    }
    
    .descripcion {
        margin: 30px;
        text-align: justify;
    }

    .detalles{
        margin-top: 48px;
    }

    button{
        width: 242px;
        height: 60px;
        border-radius: 8px;
        margin-top: 30px;
        background-color: #52E8A0;
        font-size: larger;
        border: hidden;
    }

    section{
        display: flex;
        flex-direction: row;
        justify-content: space-around;
    }

    .PerfilBasadur{
        background-color: white;
        width: 408px;
        height: 704px;
        text-align: center;
    }

    .PerfilPersonalidad{
        background-color: white;
        width: 408px;
        height: 704px;
        text-align: center;
    }
</style>