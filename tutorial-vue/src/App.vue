<template>
<div id="app" class="container">
    <div class="row">
        <div class="col-md-12">
            <h1>Grupo web</h1>
        </div>
    </div>
    <div class="row">
        <div class="col-md-12">
            <formulario-persona @add-persona="agregarPersona" />
            <tabla-personas :personas="personas" @delete-persona="eliminarPersona" @actualizar-persona="actualizarPersona" />
        </div>
    </div>
</div>
</template>

<script>
import TablaPersonas from '@/components/TablaPersonas.vue'
import FormularioPersona from '@/components/FormularioPersona.vue'
export default {
    name: 'app',
    components: {
        TablaPersonas,
        FormularioPersona,
    },
    data() {
        return {
            personas: [
                {
                    id: 1,
                    nombre: 'toni',
                    apellido: 'Nieve',
                    email: 'toni@email.com',
                },
                {
                    id: 2,
                    nombre: 'ruyou',
                    apellido: 'Lannister',
                    email: 'ruyou@email.com',
                },
                {
                    id: 3,
                    nombre: 'alexandre',
                    apellido: 'Targaryen',
                    email: 'alexandre@email.com',
                },
            ],
        }
    },
    methods: {
        agregarPersona(persona) {
            let id= 0;
            
            if (this.personas.length > 0) {
                id = this.personas[this.personas.length - 1].id + 1;
            }
            
            this.personas= [...this.personas, { ...persona, id}];
        },
        eliminarPersona(id) {
            this.personas = this.personas.filter(
                persona => persona.id !== id
            );
        },
        actualizarPersona(id, personaActualizada) {
            this.personas = this.personas.map(persona =>
                persona.id === id ? personaActualizada : persona
            )
        }
    }
}
</script>

<style>
  button {
    background: #95cdf3;
    border: 1px solid #009435;

  }
 
</style>