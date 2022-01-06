<template>
  <div class="text-center font-sans  font-bold ">
    
    <p>
        <label for="nombre">Nombre</label><br>
        <input type="text" name="nombre" v-model="nombre" class="w-60 b border-2 border-black">
    </p>
    <p class="p-8">
        <label for="contraseña">Contraseña</label><br>
        <input type="text" name="Contraseña" v-model="contraseña" class="w-60 b border-2 border-black" >
    </p>
    <p>
        <input type="button" name="nombre" value="Entrar" v-on:click="enviar" class="border-green-900 border-solid border-4 w-20 text-center ml-auto mr-auto mb-4 hover:underline hover:border-green-300 font-bold cursor-pointer">
    </p>
    <div>
      <ul>
        <li v-if="!nombreEncontrado &&appIniciada">Este usuario no esta registrado</li>
        <li v-else-if="!contEncontrada &&appIniciada">La contraseña no es correcta</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data(){
      return {
          nombre:'',
          contraseña:'',
          usuarios:[
            {nombre:'juan91',contraseña:'jmp1991'},
            {nombre:'carmen1',
            contraseña:'carmina23'},
            {nombre:'andres1',contraseña:'sito2'}
          ],
          nombreEncontrado:false,
          contEncontrada:false,
          appIniciada:false,
          j:-1
      }
  },
  methods:{
    enviar(){
      this.nombreEncontrado=false
      this.contEncontrada=false
      for(let i=0;i<this.usuarios.length;i++){
        if(this.nombre==this.usuarios[i].nombre){
          this.nombreEncontrado=true
          this.j=i
        }
        if(this.contraseña==this.usuarios[i].contraseña && i==this.j ){
          this.contEncontrada=true
        }
      }
      this.appIniciada=true
      /* this.nombre=''
      this.contraseña=''
      */
      if(this.contEncontrada==true && this.nombreEncontrado==true){
        this.$router.push('/home')
      }
      
    }
    
  }
}
</script>


<style scoped>

</style>
