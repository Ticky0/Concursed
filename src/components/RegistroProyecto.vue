<template>
        <Barnav/>
    <div class="dst-container dst-div">
        <component :is="currentTab" />
        <div class="dst-tabs-container">
            <div class="dst-tabs-item" @click="handleTabClick(tabNames.GENERAlES)"
                :class="{ 'dst-tabs-item-active': activeTabName === tabNames.GENERAlES }">
                Datos generales
            </div>
            <div class="dst-tabs-item" @click="handleTabClick(tabNames.AUTORUNO)"
                :class="{ 'dst-tabs-item-active': activeTabName === tabNames.AUTORUNO }">
                Autor 1
            </div>
            <div class="dst-tabs-item" @click="handleTabClick(tabNames.AUTORDOS)"
                :class="{ 'dst-tabs-item-active': activeTabName === tabNames.AUTORDOS }">
                Autor 2
            </div>
            <div class="dst-tabs-item" @click="handleTabClick(tabNames.ASESOR)"
                :class="{ 'dst-tabs-item-active': activeTabName === tabNames.ASESOR }">
                Asesor
            </div>
            <div class="dst-tabs-item" @click="handleTabClick(tabNames.PDF)"
                :class="{ 'dst-tabs-item-active': activeTabName === tabNames.PDF }">
                PDF
            </div>
        </div>
    </div>
</template>

<script>
import RegistroGeneral from './PestaniasRegistro/RegistroGeneral.vue';
import RegistroAutorUno from './PestaniasRegistro/RegistroAutorUno.vue';
import RegistroAutorDos from './PestaniasRegistro/RegistroAutorDos.vue';
import RegistroAsesor from './PestaniasRegistro/RegistroAsesor.vue';
import RegistroPdf from './PestaniasRegistro/RegistroPdf.vue';
import Barnav from './BarNav.vue';
// eslint-disable-next-line no-unused-vars
const tabNames = {
    GENERAlES: 'Datos generales',
    AUTORUNO: 'Autor 1',
    AUTORDOS: 'Autor 2',
    ASESOR: 'Asesor',
    PDF: 'PDF'
}
export default {
    data: () => ({
        currentTab: null,
        activeTabName: null,
        tabNames,
        tabs: {
            [tabNames.GENERAlES]: RegistroGeneral,
            [tabNames.AUTORUNO]: RegistroAutorUno,
            [tabNames.AUTORDOS]: RegistroAutorDos,
            [tabNames.ASESOR]: RegistroAsesor,
            [tabNames.PDF]: RegistroPdf
        }
    }),
    component: {
        RegistroGeneral
    },
    methods: {
        handleTabClick: function (tabNames) {
            this.activeTabName = tabNames;
            this.currentTab = this.tabs[tabNames];
        }
    },
    components: { Barnav }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Ubuntu:wght@400;500&display=swap');

.dst-div {
    font-family: 'Ubuntu', sans-serif;
    font-size: 20px;
    font-weight: 500;
}

.dst-container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    flex-direction: column-reverse;
    justify-content: center;
    align-items: center;
    text-align: center;

}

.dst-tabs-container {
    display: flex;
   
}

.dst-tabs-item {
    border-top: 8px solid #77B1FF;
    border-radius: 10px;
    padding: 10px;
    cursor: pointer;
    display: flex;
    align-items: center;
    text-align: center;
    letter-spacing: -.01em;
    
}

.dst-tabs-item-active,
.dst-tabs-item:hover {
    background-color: #77B1FF;
    color: white;
}
</style>