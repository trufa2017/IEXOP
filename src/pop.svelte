<script>
import {Button} from "svelte-mui";
export var visible;
</script>
<style>
.fondo_transparente{
    background-color: rgba(0, 0, 0, 0.281);
    width: 100vw;
    height: 100vh;
    position: fixed;
    top: 0;
    left: 0;
}
.contenedor{
   background-color:
#eae8e8;
width: 54vw;
height: 26vh;
border-radius: 15px;
padding: 15vw;
margin: 13vh auto;
}
</style>

     <!-- content here -->

<div class="fondo_transparente"  on:click={()=>{visible= false}} >


<div class="contenedor">
<table> <tr>
    <td style="width: 45%;">
 
<slot name="contenido"> </slot></td>
    <td>
    <slot name="nombre"></slot>
    <slot name="descripcion"> </slot>
    </td>
</tr></table>

<div class="centrado" style="padding-top:15vh;"><Button on:click={()=>{visible =false}}  >Ok</Button> </div>
</div>
</div>
