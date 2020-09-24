<script>
  
  import Seccion_1 from "./Seccion_1.svelte"
  import Seccion_2 from "./Seccion_2.svelte";
  import Seccion_3 from "./Seccion_3.svelte";
  import Seccion_4 from "./Seccion_4.svelte";
  import Seccion_5 from "./Seccion_5.svelte";
  import Seccion_6 from "./Seccion_6.svelte";
  import Seccion_7 from "./Seccion_7.svelte";
  import Seccion_8 from "./Seccion_8.svelte";
  import Contacto from "./_contacto.svelte";
</script>

<style>
  main {
    text-align: center;
    padding: 0px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }
.cuerpo{
  /* width:80vw; */
  /* margin:0 9vw; */
}
  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<svelte:head>
  <title>IEXOP Solutions</title>
</svelte:head>
<main>
 <div class="cuerpo">
 
  <Seccion_1 />
  <Seccion_2 />
  <Seccion_3 />
  <Seccion_4 />
  <Seccion_5 />
  <Seccion_6 />
  <Seccion_7/>
  <Seccion_8/>
<Contacto/>
 </div>

</main>

