<script setup>
import Header from './components/Header.vue'
import ItemsList from './components/ItemsList.vue';

import data from './mockup/data.json';


// Se mapea los datos del mockup para estandarizar los datos que se usarán en la app

function recursiveMapper(arr) {
  let data=[];
  let children=[];
  for (const iterator of arr) {
    if (typeof iterator === 'object') {
      for (const key in iterator) {          
          if (Array.isArray(iterator[key])){
            children.push(recursiveMapper(iterator[key]));
          }else{
            data.push({key: iterator[key]})            
          }
      }
    }else{
      null; //console.log(iterator);
    }
  }

  /*
  console.log('-----');
  console.log(data);
  console.log(children);
  */

  return {data, children}

}

const dataMapped = data.map((item) => ({
  id: item.id,
  title: item.descripcion
}))

//const newArr=recursiveMapper(data);
//console.log(newArr)

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <Header msg="Gestionar procesos"
        description="Gestionar y definir procesos para ser ejecutados en alguna plataforma" />
    </div>
  </header>

  <main>
    <h2>Process List</h2>
    <ItemsList :data="data[0].procesos" />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
