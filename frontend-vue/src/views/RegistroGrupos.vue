<template>
    <div class="block-content">
        <div style="height: 100vh; overflow: hidden;">
            <div class="min-h-screen flex relative lg:static surface-ground">
                <!-- cargando el sidebar -->
                <Sidebar></Sidebar>
                <!-- cierre del Sidebar -->

                <!-- contenedor del header y el area de trabajo -->
                <div class="min-h-screen flex flex-column relative flex-auto">
                    <HeaderWorkspace></HeaderWorkspace>

                    <!-- Inicio del cuerpo del area de trabajo -->
                    <div class="p-3 flex flex-column flex-auto">
                        <div class="border-2 border-solid surface-border border-round surface-section flex-auto">
                            <!-- Aqui va todo el contenido del area de trabajo -->
                        
                           
                                <div class="mb-1 p-4 font-bold text-2xl">
                                    <span class="text-900">Grupos de  </span>
                                    <span class="text-blue-600">estudiantes</span>
                                </div>
                                <div class="text-700 text-sm mb-6">¿Cual deseas ver?</div>
                                
                                 <div class="grid" >
                                      <div v-for="i in gruposdata" :key="id" class="col-12 md:col-6 xl:col-4 pl-4">
                                      
                                             <div class=" card-list shadow-2 border-rounded py-4 mr-5 ml-4 pl-1 p-1" >
                                               <div class=" inline flex-column align-items-start" >
                                               
                                                    <span class="p-4 ml-1 pl-4 shadow-2 mb-3 inline-block card-list" style="border-radius: 10px">
                                                        <i class="pi pi-fw pi-users  text-4xl text-blue-500"></i>
                                                    </span>

                                                    <div class="text-900 mb-3 font-medium">Grupo: {{i.nombre}}</div>
                                                    <div class="text-900 mb-3 font-medium">{{i.docente}}</div>
                                                    <div class="text-900 mb-3 font-medium">Inscritos: {{i.inscritos}}</div>
                                                    <Button label="Ver grupo"  class="mr-5 ml-2 px-4" @click="newGrupo"/>
                                                
                                               </div>
                                                <Button icon="pi pi-pencil" class="p-button-rounded p-button-success mt-4 mr-2" @click="editGrupo" />
                                                <Button icon="pi pi-trash"  class="p-button-rounded p-button-warning mt-4" @click="deletegrupo" />
                                               
                                            </div>
                                        </div>
                                    </div>
                               
                                 
                  
                    <!-- Fin del area de trabajo -->
                </div>
                <!-- fin del header y el area de trabajo-->
            </div>
        </div>   
            </div>    
    </div> 
    </div>
</template>
<script>
import Sidebar from '@/components/Sidebar.vue'
import HeaderWorkspace from '../components/HeaderWorkspace.vue'
import GrupoCrud from '../components/GrupoCrud.vue'
import Grupos from '@/service/Grupos'
import ScrollPanel from 'primevue/scrollpanel'

export default {
    props: [],
    components: {
        Grupos,
    Sidebar,
    HeaderWorkspace
},
    data(){
        GrupoCrud
        
        return {
         gruposdata:[
        {
        "id" : "1",    
        "nombre": "1 A",
        "docente": "Mrs. Tania Lopez",
        "inscritos": 30
        },
        {
        "id" : "2",  
        "nombre": "1 B",
        "docente": "Mrs. Alexandra Acevedo",
        "inscritos": 30
        },
        {
        "id" : "3",      
        "nombre": "2 A",
        "docente": "Mrs. Zara Gutierrez",
        "inscritos": 30
        },
        {
        "id" : "4",            
        "nombre": "2 B",
        "docente": "Mrs. Gloria Luna",
        "inscritos": 30
        },
        {
            "id" : "5",            
        "nombre": "3 A",
        "docente": "Mrs. Tania Lopez",
        "inscritos": 30
        },
        {
            "id" : "6",
        "nombre": "3 B",
        "docente": "Mrs. Tania Lopez",
        "inscritos": 30
        },
        {
            "id" : "7",
        "nombre": "4 A",
        "docente": "Mrs. Tania Lopez",
        "inscritos": 30
        },
        {
            "id" : "8",
        "nombre": "4 A",
        "docente": "Mrs. Tania Lopez",
        "inscritos": 30
        },
        {
            "id" : "9",
        "nombre": "5 A",
        "docente": "Mrs. Tania Lopez",
        "inscritos": 30
        },
        {
            "id" : "10",
        "nombre": "5 B",
        "docente": "Mrs. Tania Lopez",
        "inscritos": 30
        },
        {
            "id" : "11",
        "nombre": "6 A",
        "docente": "Mrs. Tania Lopez",
        "inscritos": 30
        }
    ]
        }
    },
    created(){
        this.Grupos = new Grupos();
    },
    mounted(){
    this.Grupos.getGrupos().then(gruposdata => this.Grupos = gruposdata);
    },
    methods:{
        deletegrupo(){
      Vue.delete(this.gruposdata.index, i);
        }
    }
}

</script>

<style>
</style>