<script>
  import Pop from "./pop.svelte";
  var visible = false;
  var imagen = "";
  var nombre = "";
  var descripcion = "";
</script>

<style>
  .seccion1 {
    background-image: url(imagenes/fondocarritos.jpg);
    background-size: cover;
    height: 38.5vw;
    background-repeat: no-repeat;
  }

  .tabla {
    width: 100%;
    padding: 1vw 0px 0px 0px;
  }
  .producto {
    width: 26vw;
  }
  .producto:hover {
    filter: drop-shadow(3px 3px 5px #222121eb);

    animation-name: fade_sombra;
    animation-duration: 0.5s;
    animation-timing-function: ease-out;
  }
  .barra {
   padding: 1.5vw 0 0 0;
    height: 4.5vw;
    background: linear-gradient(
      54deg,
      rgba(14, 43, 66, 1) 5%,
      rgba(0, 39, 172, 1) 100%
    );
    color: white;
    font-size: 2.2vw;
    font-weight: 400;
  }
  .tabla_menu {
    text-transform: uppercase;
    width: 100%;
    font-weight: 400;
    
  }

  .foto {
    position: absolute;
    margin: -16vw 0vw 0px -32vw;
    width: 26vw;
  }
  @keyframes fade_sombra {
    from {
      filter: drop-shadow(3px 3px 0px white);
    }
    to {
      filter: drop-shadow(3px 3px spx white);
    }
  }
</style>

<div class="seccion1" id="equipos">

  <div class="barra">
    <table class="tabla_menu">
      <tr>
        <td>C frame</td>
        <td>B frame</td>
        <td>U frame</td>
      </tr>

    </table>
  </div>
  <table class="tabla">
    <tr>
      <td
        on:click={() => {
          /*
          
          visible = true;
          imagen = 'cframe';
          nombre = 'C frame';
          descripcion = 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam officia voluptas illo ab, earum doloremque quos saepe dolore itaque quaerat tempore nostrum magnam. Omnis autem iste beatae similique, voluptate quisquam.';
          */
        }}>
        <img
          class="producto"
          src="build/imagenes/cframe.png"
          alt="foto cframe" />
      </td>
      <td
       >
        <img
          class="producto"
          src="build/imagenes/bframe.png"
          alt="foto bframe" />
      </td>
      <td
        >
        <img
          class="producto"
          src="build/imagenes/uframe.png"
          alt="foto uframe" />
      </td>
    </tr>
  </table>
</div>
{#if visible}
  <!-- content here -->

  <Pop bind:visible>

    <div slot="nombre"><span class="titulo_formularios">{nombre} </span></div>
    <div slot="contenido">
      <img class="foto" src="build/imagenes/{imagen}.png" alt="" />
    </div>
    <div slot="descripcion">{descripcion}</div>
  </Pop>
{/if}
