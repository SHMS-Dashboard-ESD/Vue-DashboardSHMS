<template>
    <div class="flex justify-between">
        <div>
            <h1 class="text-left py-3 pt-0 pb-0 text-2xl">
                <b>Daftar Customer</b>
            </h1>
        </div>
        <div class="flex items-center justify-end">
            <div class="">
                <router-link :to="('/Customer/Create')" name="id" type="button" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-full text-sm px-6 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">Add Customer</router-link>
            </div>
            <div class="w-[300px] flex justify-end pl-2">
                <!-- Search bar -->
                <form class="flex items-center w-[300px]">
                    <label for="voice-search" class="sr-only">Search</label>
                    <div class="relative w-full">
                        <div class="flex absolute inset-y-0 left-0 items-center pl-3 pointer-events-none">
                            <font-awesome-icon class="w-4 h-auto text-gray-400" icon="fa-solid fa-magnifying-glass" />
                        </div>
                        <input type="text" id="voice-search" class="bg-white border text-[#518cd5] text-sm rounded-full  block w-full pl-10 p-2.5  dark:border-gray-400 dark:placeholder-gray-400 " placeholder="Search..." required>
                    </div>
                </form>
            </div>
        </div> 
    </div>
    <div class="overflow-x-auto relative shadow-md sm:rounded-lg">
        <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
            <thead class="text-xs text-white     bg-[#1352A0] dark:bg-[#1352A0] dark:text-white">
                <tr>
                    <th scope="col" class="py-3 px-6">
                        No
                    </th>
                    <th scope="col" class="py-3 px-6">
                        Nama Customer
                    </th>
                    <th scope="col" class="py-3 px-6">
                        Perusahaan
                    </th>
                    <th scope="col" class="py-3 px-3">
                        Action
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in apilist" :key="user.id" class="bg-white border-b text-black">
                    <th scope="row" class="py-4 px-6 font-medium whitespace-nowrap">
                        {{ user.id+1 }}
                    </th>
                    <td class="py-4 px-6">
                        {{ user.fullname }}
                    </td>
                    <td class="py-4 px-6">
                        {{ user.perusahaan }}
                    </td>
                    <td class="py-2 px-3">
                        <router-link :to="('/Customer/Detail/' + user.id)" name="id" type="button" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-full text-sm px-6 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">Detail</router-link>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    import axios from "axios";
    // import BridgeShape from './BridgeShape.vue'
    


    export default {
        data(){
            return {
                apilist: [],
            }
        },
        methods: {
            
        },
        mounted(){
            let url = `${process.env.VUE_APP_URL_API}/adminCustomer/getAllCustomer`

            console.log(url)
            axios
            .get(url)
            .then(response => (this.apilist = response.data))
            .catch(error => console.log(error))
        },
    }
// export default {
//     data() {
//         return {
//             bridges: [
//                 {id: 0, name: "Jembatan Cisomang", lokasi: "Jawa Barat", rating: "9"},
//                 {id: 1, name: "Jembatan Pasupati", lokasi: "Jawa Tengah", rating: "7"},
//                 {id: 2, name: "Jembatan Ampera", lokasi: "Jawa Timur", rating: "8"},
//                 {id: 3, name: "Jembatan Suramadu", lokasi: "Kalimantan", rating: "4"},
//                 {id: 4, name: "Jembatan Barito", lokasi: "Sumatara Barat", rating: "8"},
//                 {id: 5, name: "Jembatan Merah Putih", lokasi: "Sulawesi Utara", rating: "8"},
//                 {id: 6, name: "Jembatan 5 Barelang", lokasi: "Jayapura", rating: "8"},
//                 {id: 7, name: "Jembatan Tengku Agung", lokasi: "Nusa Tenggara Barat", rating: "6"},
//                 {id: 8, name: "Jembatan Marjuwana", lokasi: "Nusa Tenggara Timur", rating: "7"},
//                 {id: 9, name: "Jembatan Suropati", lokasi: "Banten", rating: "8"},
//                 {id: 10, name: "Jembatan Kemang", lokasi: "Jakarta", rating: "9"},
//                 {id: 11, name: "Jembatan Bangka", lokasi: "Sumatra Selatan", rating: "8"},
//                 {id: 12, name: "Jembatan 3 Putri", lokasi: "Sumatra Barat", rating: "8"},
//                 {id: 13, name: "Jembatan Keder", lokasi: "Jawa Barat", rating: "7"},
//                 {id: 14, name: "Jembatan Kayu", lokasi: "Jawa Barat", rating: "9"},
//                 {id: 15, name: "Jembatan Curam", lokasi: "Jawa Barat", rating: "7"},
//                 {id: 16, name: "Jembatan Jatuh", lokasi: "Jawa Timur", rating: "5"},
//             ]
//         }
//     }
// }

</script>

<style>

</style>