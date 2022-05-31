<template>
    <SideHeader></SideHeader>
<br><br><br>
    <div class="card">
        <ToastMessage  />
        <br><br>
        <Toolbar class="mb-4">
            <template #start>
                <Button label="Nuevo Estudiante" icon="pi pi-plus" class="mr-2" @click="openModal"/>
            </template>

            <template #end>
            </template>
        </Toolbar>
        <!-- cuerpo del data table -->
         
<DataTable :value="estudiantes">
<Column v-for="col of columns" :field="col.field" :header="col.header" :key="col.field"></Column>
</DataTable>
       


    
        <!-- fin del cuerpo del data table -->
    </div>
    <!-- modal para agregar estudiantes -->
    <Dialog header="Agregar nuevo estudiante" v-model:visible="displayModal" :style="{width: '50vw'}" :modal="true">
            <p class="m-0">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco
                laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
            <template #footer>
                <Button label="Cancelar" icon="pi pi-times" @click="closeModal" class="p-button-text"/>
                <Button label="Guardar" icon="pi pi-check" @click="saveInfo" autofocus />
            </template>
    </Dialog>
</template>

<script>
import SideHeader from '@/components/SideHeader.vue'
import InformacionEstudiantes from '@/service/InformacionEstudiantes'
export default {

    components: {
        SideHeader,
        //usamos la importacion
        InformacionEstudiantes
    }, 
    data(){
        return {
            displayModal: false,
            messages: [],
            columns:null,
            estudiantes:null
        }
    },
    InformacionEstudiantes:null,
    created(){
        this.InformacionEstudiantes = new InformacionEstudiantes();
        this.columns = [
            //el field es el elemento dentro del json, o sea, la variable
            //el header es lo que se muestra en la pantalla
    {field:"id", header:"ID"},
    {field:"nombre", header:"Nombre"},
    {field:"apellidos", header:"Apellidos"},
    {field:"grupo", header:"Grupo"},
    {field:"correo",header:"Correo"},
    //aqui lleva un punto direccion, por que dentro de ella hay ciudad y nacionaliodad, y solo ocuparemos ciudad
    {field:"direccion.ciudad",header:"Dirreccion"}
        ]

    },

    mounted(){
        //como estaba nulo le asignamos el listado de estudiantes segun la api
        this.InformacionEstudiantes.getStudents().then(data => this.estudiantes = data);
    },
    computed:{
        bindings(){
            return {
                columns:['id','nombre','apellidos'],
                data:[
                    {"id":12, "nombre":"saul isaac", "apellidos":"lopez rios"}
                    ]
            }
        }
    },
    methods: {
        openModal(){
            this.displayModal = true
        },
        closeModal(){
            this.displayModal = false
        },
        saveInfo(){
            this.displayModal = false
            this.$toast.add({severity: 'success', summary: 'Agregado con Exito', detail: 'El estudiante ha sido agregado con exito.', life: 3000});

        }
    }
    
}


</script>