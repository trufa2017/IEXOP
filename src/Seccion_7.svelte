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
    height: 39vw;
    background-repeat: no-repeat;
  }

  .tabla {
    width: 100%;
    padding: 1vw 0px;
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
  .producto_2 {
    width: 32vw;
  }
   .producto_2:hover {
    filter: drop-shadow(3px 3px 5px #222121eb);

    animation-name: fade_sombra;
    animation-duration: 0.5s;
    animation-timing-function: ease-out;
  }
  .barra {
    padding: 1.2vw 0 0 0;
    height: 7vw;
    background: linear-gradient(
      54deg,
      rgba(14, 43, 66, 1) 5%,
      rgba(0, 39, 172, 1) 100%
    );
    color: white;
    font-size: 4.2vw;
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
    width: 44vw;
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

<div class="seccion1">

  <div class="barra">
    <table class="tabla_menu">
      <tr>
        <td>Equipos de Arrastre</td>
      </tr>

    </table>
  </div>
  <table class="tabla">
    <tr>
      <td
       >
        <img
          class="producto"
          src="build/imagenes/carrito1.png"
          alt="foto carrito1" />
      </td>
      <td
       >
        <img
          class="producto_2"
          src="build/imagenes/carrito2.png"
          alt="foto combcarts" />
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
