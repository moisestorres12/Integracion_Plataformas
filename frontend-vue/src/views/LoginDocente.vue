<template>

<div class="field" style="background-color:#CFDDF5;">
<div height="20px"><br></div>

<div class="grid">
    <div class="col">
         <div class="flex align-items-center justify-content-center flex-wrap card-container blue-container">
        <div class="surface-card p-5 shadow-4 border-round w-full lg:w-10">
    <div class="text-center mb-5">
        <div class="text-900 text-3xl font-medium mb-3">Inicia Session con una de tus cuentas.</div>
        <span class="text-600 font-medium line-height-3"></span>
        <a class="font-medium no-underline ml-2 text-blue-500 cursor-pointer"></a>
    </div>

    <div>
        <Button label="Iniciar con Google" icon="pi pi-google" class="w-full b button-danger" />
       <hr>
        <Button label="Iniciar con Google" icon="pi pi-google" class="w-full b p-button-danger" />

    </div>


        </div>
    </div>
    </div>
    <div class="col">
         <div class="flex align-items-center justify-content-center flex-wrap card-container blue-container">
        <div class="surface-card p-5 shadow-4 border-round w-full lg:w-11">
    <div class="text-center mb-5">
        <Image src="../img/logo.png" alt="logo del colegio" height="75" class="mb-3" />
        <div class="text-900 text-3xl font-medium mb-3">Bienvenido Educador</div>
        <span class="text-600 font-medium line-height-3"></span>
        <a class="font-medium no-underline ml-2 text-blue-500 cursor-pointer"></a>
    </div>

    <div>
        <label for="email1" class="block text-900 font-medium mb-2"><strong>Email</strong></label>
        <InputText id="email1" type="text" class="w-full mb-3" />

        <label for="password1" class="block text-900 font-medium mb-2"><strong>Password</strong></label>
        <InputText id="email1" type="password" class="w-full mb-3" />
        <div class="flex align-items-center justify-content-between mb-6">
            <div class="flex align-items-center">
                <Checkbox id="rememberme1" :binary="true" v-model="checked" class="mr-2" />
                <label for="rememberme1"></label>
            </div>
            <a class="font-medium no-underline ml-2 text-blue-500 text-right cursor-pointer">¿Olvido su Contraseña?</a>
        </div>

        <Button @click="goToPrincipal" label="Iniciar Sesion" icon="pi pi-user" class="w-full" />
        <hr>

    </div>


        </div>
    </div>
    </div>
</div>
    
    <div height="20"><br></div>
</div>    

</template>

<script>

export default {
    data(){
        return {
            value1: null
        }
    },
    methods: {
        goToPrincipal(){
            this.$router.push('/principal')
        }
    }
}
</script>
<style>

</style>