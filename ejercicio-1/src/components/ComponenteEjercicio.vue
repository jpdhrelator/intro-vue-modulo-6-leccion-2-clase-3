<template >
    <h1>{{ titulo }}</h1>
    <div>
        <form>
            <div class="mb-3">
                <label class="form-label">Marca</label>
                <input type="text" class="form-control" v-model="marca" >
            </div>
            <div class="mb-3">
                <label class="form-label">Modelo</label>
                <input type="text" class="form-control" v-model="modelo" >
            </div>
            <div class="mb-3">
                <label class="form-label">Patente</label>
                <input type="text" class="form-control" v-model="patente" >
            </div>
            
            <div v-if="error" class="alert alert-danger" role="alert">
                Patente ya Existe!!!!
            </div>
          
            <button type="button" @click="guardar" class="btn btn-primary">Guardar</button>
        </form>
        <table class="table">
            <thead>
                <tr>
                <th scope="col">#</th>
                <th scope="col"></th>
                <th scope="col">First</th>
                <th scope="col">Last</th>
                <th scope="col">Handle</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(vehiculo, index) in vehiculos" :key="vehiculo.patente">
                <th scope="row">{{ index+1 }}</th>
                <td>
                    <div class="row">
                        <div class="col-md-4">
                            <button type="button" @click="editarVehiculo(vehiculo.patente)"  class="btn btn-primary">Editar</button>
                        </div>
                        <div class="col-md-4">
                            <button type="button" @click="eliminarVehiculo(vehiculo.patente)" class="btn btn-danger">Borrar</button>
                        </div>
                        <div v-if="!vehiculo.vendido" class="col-md-4">
                            <button type="button" @click="vehiculo.vendido= true" class="btn btn-success">Vendido</button>
                        </div>

                    </div>
                    
                </td>
                <td>{{ vehiculo.marca }}</td>
                <td>{{ vehiculo.modelo }}</td>
                <td>{{ vehiculo.patente }}</td>
                <td>
                    <span :class="vehiculo.vendido? 'text-bg-success': 'text-bg-primary'" 
                            class="badge ">
                        <!--  otra opcion para lo mismo   
                            <b v-if="vehiculo.vendido">Vendido</b>
                            <b v-else>Disponible</b>
                        -->
                        {{ vehiculo.vendido ? 'Vendido' : 'Disponible '}}
                    </span>
                </td>
                </tr>
            
            </tbody>
        </table>
        <div class="card" style="width: 18rem;">
            <div class="card-header">
                Estadisticas
            </div>
            <ul class="list-group list-group-flush">
                <li class="list-group-item">Total Disponibles: {{ contarVehiculos('disponibles') }}</li>
                <li class="list-group-item">Total Vendidos: {{ contarVehiculos('vendidos') }}</li>
                <li class="list-group-item">Total: {{ contarVehiculos() }}</li>
            </ul>
        </div>
    </div>
</template>
<script setup>
import { ref } from 'vue';
    const vehiculos=ref([
        {marca:"Subaru",modelo:"Legacy", patente:"XXXX-10",vendido:false},
        {marca:"Toyota",modelo:"Yaris", patente:"XXXX-11",vendido:false},
        {marca:"Mazda",modelo:"Auris", patente:"XXXX-12",vendido:false},
    ]);
    let titulo="Titulo"
    let patente = ref('');
    let modelo = ref('');
    let marca = ref('');
    let error = ref(false);
    function eliminarVehiculo(patente) {
        console.log(patente);
        
        vehiculos.value= vehiculos.value.filter((ve)=> ve.patente!=patente);
    }
    function editarVehiculo(inPatente) {
        patente.value=inPatente;
    }
    /*
    const contarVendidos=()=> vehiculos.value.filter((ve)=> ve.vendido).length;
    const contarDisponibles=()=> vehiculos.value.filter((ve)=> !ve.vendido).length;
    const contarTodos=()=> vehiculos.value.length;
*/
    const contarVehiculos= (tipo='todos')=>{
        if(tipo=='disponible'){
            return vehiculos.value.filter((ve)=> !ve.vendido).length
        }else if(tipo=='vendidos'){
            return vehiculos.value.filter((ve)=> ve.vendido).length;
        }else {
            return vehiculos.value.length
        }
    }

    function guardar(){
        if(vehiculos.value.filter((ve)=> ve.patente==patente.value).length > 0){
            error.value = true;
            return;
        }
        error.value = false;
        vehiculos.value.push({
            marca,
            modelo,
            patente
        });
        
        /*
        lo de arriba es lo misom que hacer esto
        {
            marca:marca,
            modelo:modelo,
            patente:patente
        }
        */
    }

</script>
<style >
    
</style>