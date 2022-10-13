<script setup>
  import { onMounted, ref } from 'vue';

  import PaginatePost from './components/Composition/PaginatePost.vue';
  import BlogPost from './components/Composition/BlogPost5.vue'
  import LoadingSpinner from './components/Composition/loadingSpinner.vue';

  const posts = ref([]);
  const favorito = ref("");

  const postXpage = 10;
  const inicio = ref(0);
  const fin = ref(postXpage);
  const loading = ref(true);

  const cambiarFavorito = (title) => {
    favorito.value=title;
  }

  const next = () => {
    inicio.value += postXpage;
    fin.value += postXpage;
  }

  const prev = () => {
    inicio.value += -postXpage;
    fin.value += -postXpage;
  }

  //fetch('https://jsonplaceholder.typicode.com/posts')
  //  .then(res => res.json())
  //  .then( (data) => posts.value = data)
  //  .catch((e)=>console.log(e))
  //  .finally(()=> {
  //    setTimeout(() => {
  //      loading.value=false;
  //    }, 500);
  //  });

  const fetchData = async () => {
    try {
      const res = await fetch('https://jsonplaceholder.typicode.com/posts');
      posts.value = await res.json();
    } catch (error) {
      console.log(error);
    } finally {
      setTimeout(() => {
        loading.value=false;
      }, 500);
    }
  }

  onMounted(async() =>{
    fetchData();
  });


</script>

<template>
  <LoadingSpinner v-if="loading"/>
  <div class="container" v-else>
    <h1>APP</h1>
    <h2>Mis Post Favoritos: <span class="text-success"> {{ favorito }} </span></h2>

    <PaginatePost class="mb-2"
      @AvanzarPagina='next'
      @RetrocederPagina='prev'
      :inicio="inicio"
      :fin="fin"
      :maxLength="posts.length"
    >
    </PaginatePost>

    <BlogPost 
      v-for="post in posts.slice( inicio, fin)"
      :key="post.id"
      :title="post.title" 
      :id=post.id 
      :body=post.body 
      :colorText=post.colorText
      @cambiarFavoritoNombre='cambiarFavorito'
    >
    </BlogPost>

  </div>
</template>
