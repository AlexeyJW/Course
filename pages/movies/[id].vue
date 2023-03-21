<script setup>
const route = useRoute()
// const {data}=useAsyncData(`/movies/${route.params.id}`,()=>{
//     return $fetch(`http://www.omdbapi.com/?apikey=8e3f600b&i=${route.params.id}`);
// },
//     {
//       pick:["Plot", "Title"]
//     }
// )
// ************2=============
// const {data}=useFetch(`http://www.omdbapi.com/?apikey=8e3f600b&i=${route.params.id}`,
// {
//     pick:["Plot", "Title"],
//     key:`/movies/${route.params.id}`,
//     onResponse({request, response}){
//         if (response._data.Error==="Incorrect IMDb ID."){
//             showError({statusCode:404, statusMessage:"Page Not Found"})
//         }
//     },
// })
//========3==================
const {data, error} = await useFetch(`http://www.omdbapi.com/?apikey=8e3f600b&i=${route.params.id}`,
        {
            pick: ["Plot", "Title", "Error"],
            key:`/movies/${route.params.id}`,
        }
);
if (error.value){
    //handle accordingly
}
if (data.value.Error==="Incorrect IMDb ID."){
    showError({statusCode:404, statusMessage:"Page Not Found"});
}
//SEO
useHead({
    title:data.value.Title
})
</script>
<template>
    <div>
        <pre>{{ data }}</pre>
    </div>
</template>