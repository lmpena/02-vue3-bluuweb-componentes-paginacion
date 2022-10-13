<script setup>
 
  import CompositionButtonCounter from './components/Composition/ButtonCounter.vue';
  import CompositionBlogPost from './components/Composition/BlogPost.vue';
  import CompositionBlogPost2 from './components/Composition/BlogPost2.vue';
  import CompositionBlogPost3 from './components/Composition/BlogPost3.vue';
  import CompositionBlogPost4 from './components/Composition/BlogPost4.vue';
  import OptionButtonCounter from './components/Option/ButtonCounter.vue';
  import OptionBlogPost from './components/Option/BlogPost.vue';

  import { ref } from 'vue';

  //const posts = ref( [
  //  {title: 'Post 1', id: 1, body: 'descricion 1', colorText: 'primary'},
  //  {title: 'Post 2', id: 2, body: 'descricion 2', colorText: 'secondary'},
  //  {title: 'Post 3', id: 3, body: 'descricion 3', colorText: 'success'},
  //  {title: 'Post 4', id: 4, body: 'descricion 4', colorText: 'warning'},
  //  {title: 'Post 5', id: 5, body: 'descricion 5', colorText: 'info'},
  //]);

  const posts = ref([]);

  const favorito = ref("");

  const cambiarFavorito = (title) => {
    favorito.value=title;
  }

  fetch('https://jsonplaceholder.typicode.com/posts')
    .then(res => res.json())
    .then( (data) => posts.value = data);

</script>

<template>
  <div class="container">
    <h1>APP</h1>
    <h2>Mis Post Favoritos: <span class="text-success"> {{ favorito }} </span></h2>

<!--
    <CompositionButtonCounter/>
    <OptionButtonCounter/>
-->

<!--
    <CompositionBlogPost title="Post Compsition 1" id="1" body="descripcion Compsition 1" colorText="primary" />
    <CompositionBlogPost title="Post Compsition 2" id="2" body="descripcion Compsition 2" colorText="secondary" />
    <CompositionBlogPost title="Post Compsition 3" id="3" body="descripcion Compsition 3" colorText="success" />
    <CompositionBlogPost title="Post Compsition 4" id="4" body="descripcion Compsition 4" colorText="warning" />

    <OptionBlogPost title="Post Option 1" id="1" body="descripcion Option 1" colorText="primary" />
    <OptionBlogPost title="Post Option 2" id="2" body="descripcion Option 2" colorText="secondary" />
    <OptionBlogPost title="Post Option 3" id="3" body="descripcion Option 3" colorText="success" />
    <OptionBlogPost title="Post Option 4" id="4" body="descripcion Option 4" colorText="warning" />
-->

<!-- 
    <CompositionBlogPost2 
      v-for="post in posts"
      :key="post.id"
      :title="post.title" 
      :id=post.id 
      :body=post.body 
      :colorText=post.colorText>
    </CompositionBlogPost2>
-->

<!-- 
    <CompositionBlogPost3 
      v-for="post in posts"
      :key="post.id"
      :title="post.title" 
      :id=post.id 
      :body=post.body 
      :colorText=post.colorText
      @cambiarFavoritoNombre='cambiarFavorito'
    >
    </CompositionBlogPost3>
-->

    <CompositionBlogPost4 
      v-for="post in posts"
      :key="post.id"
      :title="post.title" 
      :id=post.id 
      :body=post.body 
      :colorText=post.colorText
      @cambiarFavoritoNombre='cambiarFavorito'
    >
    </CompositionBlogPost4>

  </div>
</template>
