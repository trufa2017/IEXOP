<script>
  import { blur } from "svelte/transition";
  import { onMount } from "svelte";
  import { fly, fade } from "svelte/transition";
  onMount(() => {
    setInterval(() => {
      nada_visible = true;
      
      setTimeout(() => {
        nada_visible = false;
      }, 100);
      if (diapositiva_visible == 2) {
        diapositiva_visible = 1;
        return;
      }
      diapositiva_visible++;
    }, 10000);
  });
  var visible = false;
  var diapositiva_visible = 1;
  let nada_visible = false;
</script>

<style>
  .seccion1 {
    background-image: url(imagenes/seccion1.jpg);
    background-size: cover;
   height: 92.4vw;
    background-repeat: no-repeat;
  }
  .menu {
    margin: 0 0vw;
    position: absolute;
    width: 100vw;
    color: #095ca2;
    padding: 2vw 14vw;
    font-size: 1.5vw;
  }
  .menu_div {
    max-width: 800px;
  }
  .equis {
    position: absolute;
    left: 0px;
    margin: 7.2vw -12px;
    width: 100vw;
    filter: brightness(1);

    animation-name: equis;
    animation-duration: 2s;
  }
  .diapositiva {
    height: 7vw;
    width: 59vw;
    padding: 4vw;
    color: white;
    font-size: 1.6vw;
    font-weight: 400;
    background: rgb(46, 210, 255);
     text-transform: uppercase;
    background: linear-gradient(
      164deg,
      rgba(46, 210, 255, 1) 5%,
      rgba(43, 97, 214, 0.44439782749037116) 100%
    );
  }
  .diapositivas {
    padding-top: 70vw;
    padding-left: 15vw;
  }

  @keyframes equis {
    from {
      filter: brightness(0);
    }
    to {
      filter: brightness(1);
    }
  }
</style>

<div class="seccion1" id="seccion1">
  <div class="">

    <table class="menu">

      <tr>
        <td>
          <a href="#flujo" class="menu-item">FLUJO</a>
        </td>
        <td>|</td>
        <td>
          <a href="#equipos" class="menu-item">EQUIPOS</a>
        </td>
        <td>|</td>
        <td>
          <a href="#contacto" class="menu-item">CONTACTO</a>
        </td>
        <td>|</td>
        <td>
          <a href="#principios" class="menu-item">PRINCIPIOS</a>
        </td>
      </tr>
    </table>
    <div class="diapositivas">

      {#if nada_visible}
        <!-- content here -->
      {:else}
        <!-- else content here -->

        {#if diapositiva_visible === 1}
          <!-- content here -->
          <div class="diapositiva" in:fly={{duration:500 , x:10}}>
            Creamos entornos en donde el flujo de ideas y productos provoca que
            los desperdicios sean cosa del pasado
          </div>
        {:else}
          <!-- else content here -->
          <div class="diapositiva" in:fly={{duration:500 , x:10}}>
            Un flujo continuo de materiales contribuye a la elimincación de
            desperdicios, al incremento de la productividad, aumento en la
            satisfacción de los colaboradores y a la construcción de una cultura
            de excelencia.
          </div>
        {/if}
      {/if}
    </div>
  </div>

  <!--  
{#if visible}
     
     <div out:blur={{amount:3 , duration:500}}>
     <img class="equis" src="build/imagenes/equis.png" alt=""/>
     </div>
{/if}

 -->

</div>
