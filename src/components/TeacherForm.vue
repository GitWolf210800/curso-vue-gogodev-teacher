<template>
    <section>
        <h3>Añadir Profesor</h3>
        <div><label>Nombre:</label> <input type="text" v-model="teacher.teacherName"></div>
        <div><label>Apellido:</label> <input type="text" v-model="teacher.surname"></div>
        <div><label>DNI / NIF:</label> <input type="text" v-model="teacher.dni"></div>
        <div><label>Materias:</label> <input type="text" v-model="subject"></div>
        <div>
            <ul>
                <li v-for="(elm, index) in teacher.subjects" :key="index">{{ elm }}</li>
            </ul>
        </div>
        <input type="checkbox" v-model="teacher.doc">Documentación Entregada
        <button @click="handleSubject">Agregar</button>
    </section>
        <h3>Listado de Profesores</h3>
    <section>

    </section>
</template>

<script lang="ts" setup>
import { Ref, ref } from 'vue';

interface ITeacher {
    teacherName: string,
    surname: string,
    dni: string, 
    subjects: Array<string>,
    doc: boolean
}

let teacher:Ref<ITeacher> = ref({
    teacherName: '',
    surname: '',
    dni: '',
    subjects: [],
    doc: false
})

let teachers:Ref<Array<ITeacher>> = ref([]);

let subject:Ref<string> = ref('');

const handleSubject = () => {
    teacher.value.subjects.push(subject.value)
};
</script>

<style scoped>
</style>