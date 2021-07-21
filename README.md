# vueSecondApp
*Версия на русском курсивом*


### According to Vue Handbook:
*Согласно книге Vue Handbook*

https://flaviocopes.nyc3.digitaloceanspaces.com/vue-handbook/vue-handbook.pdf

## install vue-cli if not installed
*Установите vue-cli, если еще не установлен*

`npm install -g @vue/cli`

## Create app
*Создайте приложение*

`vue create vuesecondapp`

## The files structure
*Структура файлов*

Beside package.json , which contains the configuration, these are the files contained in the initial project structure:\
*Помимо package.json , который содержит конфигурацию, есть ряд других файлов:*

- public/index.html
- src/App.vue
- src/main.js
- src/assets/logo.png
- src/components/HelloWorld.vue

### index.html
The index.html file is the main app file.\
*index.html - это основной файл приложения*

In the body it includes just one simple element:\
*В body есть один простой элемент:*
`<div id="app"></div>` . 

This is the element the Vue application will use to attach to the DOM.\
*Это элемент, которые Vue приложение использует для подключения к DOM.*

~~~html
 <!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <title>CodeSandbox Vue</title>
</head>
<body>
  <div id="app"></div>
  <!-- built files will be auto injected -->
</body>
</html>
~~~

### src/main.js
This is the main JavaScript files that drive our app.\
*Это основной файл JavaScript, который управляет нашим приложением*

We first import the Vue library and the App component from App.vue .\
*В первую очередь мы импортируем библиотеку Vue и компонент App из App.vue .*

We set productionTip to false, just to avoid Vue to output a "you're in development mode" tip in the console.\
*Устанавливаем productionTip в false - просто чтобы Vue не выводил "you're in development mode" в консоль.*

Next, we create the Vue instance, by assigning it to the DOM element identified by #app , which we defined in index.html , and we tell it to use the App component.\
*Далее мы создаем экземпляр Vue, прикрепляясь к элементу DOM #app, который мы определили в index.html.*

~~~js
 // The Vue build version to load with the `import` command
// (runtime-only or standalone) has been set in webpack.base.conf with an alias.
import Vue from 'vue'
import App from './App'

Vue.config.productionTip = false

/* eslint-disable no-new */
new Vue({
  el: '#app',
  components: { App },
  template: '<App/>'
})
~~~

###src/App.vue

~~~vue
<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
~~~

App.vue is a Single File Component. It contains 3 chunks of code: HTML, CSS and JavaScript.\
*App.vue - это однофайловый компонент (Single File Component). В нем три куска кода: HTML, CSS and JavaScript.*

This might seem weird at first, but Single File Components are a great way to create self- contained components that have all they need in a single file.\
*Это может показаться тупо, но Single File Component - хороший путь для создания компонентов, которые содержат все в одном месте в одном файле.*

We have the markup, the JavaScript that is going to interact with it, and style that's applied to it, which can be scoped, or not. In this case, it's not scoped, and it's just outputting that CSS which is applied like regular CSS to the page.\
*У нас есть разметка, JavaScript, который будет взаимодействовать с ней, и стили, которые применяются к разметке.*

The interesting part lies in the script tag.\
*Интересные строки в тэге script .*

We import a component from the components/HelloWorld.vue file, which we'll describe later.\
*Мы импортируем компонент из файла components/HelloWorld.vue, который будет описан ниже.*

This component is going to be referenced in our component. It's a dependency. We are going to output this code:\
*Этот компонент будет использоваться в нашем компоненте. Это зависимость (dependency). Мы выведем следующий код:*

~~~vue
 <div id="app">
  <img width="25%" src="./assets/logo.png">
  <HelloWorld/>
</div>
~~~

from this component, which you see references the HelloWorld component. Vue will automatically insert that component inside this placeholder.\
*из этого компонента, который, как мы видим, ссылается на компонент HelloWorld. Vue автоматически вставит этот компонент внутрь плейсхолдера (placeholder).*

###src/components/HelloWorld.vue
Here's the HelloWorld component, which is included by the App component. This component outputs a set of links, along with a message.\
*Ниже компонент HelloWorld, который вставлен в компонент App. Этот компонент выводит набор ссылок вместе с сообщением.*

Remember above we talked about CSS in App.vue, which was not scoped? The HelloWorld component has scoped CSS.\
You can easily determine it by looking at the style tag. If it has the scoped attribute, then it's scoped: `<style scoped>`\
This means that the generated CSS will be targeting the component uniquely, via a class that's applied by Vue transparently. You don't need to worry about this, and you know the CSS won't leak to other parts of the page.\
*Файл HelloWorld имеет отдельно выделенный CSS (в теге style).*

The message the component outputs is stored in the data property of the Vue instance, and outputted in the template as {{ msg }} .\
*Сообщение, которое выводит компонент, хранится в свойстве data в экземпляре Vue и выводится в шаблон, как {{ msg }} .*

Anything that's stored in data is reachable directly in the template via its own name. We didn't need to say data.msg , just msg .\
*Все, что хранится в data, доступно напрямую в шаблоне по его имени. Нам не нужно писать data.msg - просто msg.*

~~~vue
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
~~~

## Project setup
*Установка проекта*
```shell
npm install
```

### Compiles and hot-reloads for development
*Собрать и перезапустить проект для разработки*
```shell
npm run serve
```

### Compiles and minifies for production
*Собрать и минифицировать для продакшна*
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).