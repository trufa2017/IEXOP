<script>
  import { onMount } from "svelte";
  import { postDataContacto } from "./stores";
  import { Textfield, Button, Snackbar } from "svelte-mui";

  var enviado = false;
  var error = false;
  var nombre ='';
  var apellido ='';
  var email = '';
  var telefono = '';
  var descripcion='';
  let visible_error=false;
  let visible_faltante=false;
  let visible_exito=false;
  let mensaje= ''
  onMount(() => {
    const formElement = document.querySelector("#contact-form");
    formElement.addEventListener("submit", event => {
      event.preventDefault();
     
      
      let falta = checar_si_esta_completo();
       console.log(falta);
      if(falta.length>0){
        mensaje = 'Falta :'+ falta;
        visible_faltante= true;
        return;
      }
      const data = new URLSearchParams(new FormData(formElement));
       console.log(data);
      var url = "https://getform.io/f/45434f1a-7e80-4619-9658-b356a2f8fd41";
      fetch(url, {
        method: "post",
        body: data
      })
        .then(respuesta => {
          console.log(respuesta);
          enviado = true;
          visible_exito= true;
        })
        .catch(err => {
          console.log(err);
          visible_error= true;
        });
    });
  });

  function checar_si_esta_completo() {
    let falta=''
    if(nombre===''){
      falta += 'Nombre ' ;
    }
    if(apellido===''){
      falta += 'Apellido ' ;
    }
    if(email===''){
      falta += 'Email ' ;
    }
    if(telefono===''){
      falta +='Teléfono ' ;
    }
    if(descripcion===''){
      falta +='Descripción ' ;
    }
    return falta;
  }
</script>

<style>
  .contacto {
    text-align: left;
   margin: -1vw auto;
    color: white;
    height: 59vw;
    background-image: url(imagenes/contacto_back.jpg);
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    height: 70vw;
  }
  .grid-container {

    padding-top:15vw;
    display: grid;
    grid-template-columns: 0.3fr 1.8fr 0.4fr 2.2fr 0.3fr;
    grid-template-rows: 6.5vw 6.5vw 6.5vw;
    grid-template-areas: "margen1 nombre margen2 telefono margen3" "margen1 apellido margen2 ayuda margen3" "margen1 email margen2 ayuda margen3";
  }

  .nombre {
    grid-area: nombre;
  }

  .margen1 {
    grid-area: margen1;
  }

  .margen2 {
    grid-area: margen2;
  }

  .apellido {
    grid-area: apellido;
  }

  .telefono {
    grid-area: telefono;
  }

  .ayuda {
    grid-area: ayuda;
  }

  .email {
    grid-area: email;
  }

  .margen3 {
    grid-area: margen3;
  }

 
  .input_main {
    background-color: #00000c36;
    border-radius: 7px;
    border: 1px solid #202931;
    color: white;
    width: 96%;
    height: 50%;
    padding-left: 1vw;
    font-size: 1.5vw;
  }


  .input_main_area {
    background-color: #00000c36;
    border-radius: 7px;
    border: 1px solid #202931;
    color: white;
    width: 96%;
    height: 10vw;
    padding-left: 1vw;
    font-size: 1.5vw;
  }
  .botton_enviar{
    position: absolute;
    bottom: 24vw;

    width: 100%;
  }
  .mensaje_exito{
    height: 46vw;
    background-color: #00010a;
    color: white;
    background-image: url(build/imagenes/contacto_back.jpg);
    background-image: url(imagenes/contacto_back.jpg);
    background-position: center;
    background-repeat: no-repeat;
    background-size: contain;
    padding-top: 22vw;
  }
</style>

{#if error == true}
  <!-- Error al mandar form -->
<div class="centrado" style="color:white;">
Se ha detectado un error, por favor, inténtelo más tarde, ó
  contactenos al +52 (442) 478 0937
</div>
{:else}
  <!-- Todo normal -->
  {#if enviado}
    <!-- Ya enviado  -->
  <div class="centrado mensaje_exito" >
   Hemos recibido su mensaje, gracias, a la brevedad, se pondrá en contacto con
    usted alguno de nuestros asesores.
  </div>
  {:else}
    <div class="contacto" id="contacto">
      <form
        id="contact-form"
        action="https://getform.io/f/45434f1a-7e80-4619-9658-b356a2f8fd41"
        method="POST">
        <div class="grid-container">
          <div class="nombre">
            <label for="name">Nombre</label>
            <input bind:value={nombre} tabindex="1" filled type="text" name="name" class="input_main" />
          </div>
          <div class="margen1" />
          <div class="margen2" />
          <div class="apellido">
            <label for="name">Apellido</label>
            <input bind:value={apellido} tabindex="2" filled type="text" name="apellido" class="input_main" />
          </div>
          <div class="telefono">
            <label for="name">Teléfono</label>
          <input bind:value={telefono} tabindex="4" filled type="text" name="telefono" class="input_main" />
          </div>
          <div class="ayuda">
            <label for="name">En qué podemos ayudarte ?</label>
            <textarea
            tabindex="5"
            bind:value={descripcion}
              name="descripcion"
              class="input_main_area"
              cols="50"
              rows="5" />
          </div>
          <div class="email">
            <label for="name">Email</label>
            <input bind:value={email} tabindex="3" filled type="email" name="email" class="input_main" />
          </div>
          <div class="margen3" />
        </div>
         <div class="centrado botton_enviar">
        <Button  tabindex="6" raised color="primary" type="submit">enviar</Button>
      </div>
      </form>     
    </div>
  {/if}
{/if}

<Snackbar bind:visible={visible_faltante} bg="red">
     {mensaje}
    <span slot="action">
        <Button color="black" on:click={() => (visible_error = false)}>Cerrar</Button>
    </span>
</Snackbar>


<Snackbar bind:visible={visible_error} bg="darkorange">
      Se ha detectado un error, por favor, inténtelo más tarde, ó
  contactenos al +52 (442) 478 0937
    <span slot="action">
        <Button color="black" on:click={() => (visible_error = false)}>Cerrar</Button>
    </span>
</Snackbar>


<Snackbar bind:visible={visible_exito} bg='black'>
    Hemos recibido su mensaje, gracias, a la brevedad, se pondrá en contacto con
    usted alguno de nuestros asesores.
    <span slot="action">
        <Button color="white" on:click={() => (visible_error = false)}>Cerrar</Button>
    </span>
</Snackbar>