<template>
    <div class="w-full h-full flex justify-center items-center">
        <div class="flex flex-col">
            <div class="flex-col flex mb-32">
                <input type="file" id="file" name="file" class="hidden" @change="handleFileUpload">
                <label for="file" class="border border-dashed border-stone-300 px-9 py-7">
                    <span class="text-white text-lg sm:text-4xl">Chercher le fichier à partager</span>
                </label>
                <div class="flex">
                    <button @click="toggleListe()"
                        class="bg-indigo-600 text-white px-8 py-2 mt-5 uppercase font-semibold">
                        Destinataires
                        <i class="fas fa-users"></i>
                    </button>
                    <button @click="uploadFile()"
                        class="bg-transparent border border-dashed rounded-lg ml-3 text-white px-8 py-2 mt-5 uppercase font-semibold">
                        Uploader
                    </button>
                </div>
            </div>
        </div>
    </div>
    <div v-if="show_popup" class="fixed top-0 left-0 w-full h-full flex items-center justify-center" id="list_pers">
        <div>
            <div @click="show_popup = false" class="bg-transparent z-0 absolute h-full w-full top-0 left-0"></div>
            <div class="flex z-50">
                <list_personnel></list_personnel>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import list_personnel from '@/components/list_personnel.vue';

export default {
    components: {
        list_personnel,
    },
    data() {
        return {
            show_popup: false,
            selectedFile: null, // Définir selectedFile dans data
        };
    },
    methods: {
        handleFileUpload(event) {
            this.selectedFile = event.target.files[0]; // Capturer le fichier sélectionné
        },
        toggleListe() {
            this.show_popup = true;
        },
        async uploadFile() {
            if (!this.selectedFile) {
                console.error("Aucun fichier sélectionné");
                return;
            }

            const formData = new FormData();
            formData.append('file', this.selectedFile);

            try {
                const response = await axios.post('api/upload', formData, {
                    headers: {
                        'Content-Type': 'multipart/form-data',
                    },
                });
                console.log(response.data); // Gérer la réponse
            } catch (error) {
                console.error('Erreur lors du téléversement:', error);
            }
        },
        async getFile() {
            try {
                const response = await axios.get('api/liste');
                console.log(response.data); // Gérer la réponse
            } catch (error) {
                console.error('Erreur lors de la récupération des fichiers:', error);
            }
        },
    },
    mounted() {
        this.getFile();
    },
};
</script>

<style scoped>
#list_pers {
    background: rgba(0, 0, 0, 0.698);
}
</style>
