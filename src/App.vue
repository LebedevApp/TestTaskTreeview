<template>
  <div id="app">
    <section class="header">
      <h1>The treeview</h1>
    </section>
    <main>
      <router-view />
    </main>
    <footer>
      <section class="container">
        <h2>Задание:</h2>
        <pre>
{
name: 'root',
selected: false,
childred: [
{
name: 'item1',
selected: true,
children: [
....
]
},
{
name: 'item2',
seelcted: false
children: [
....
]
},
...
]
}</pre
        >
        <p>1-й компонент отображает списком все элементы, у которых selected = true. Из него можно удалить любой элемент (у элемента кнопка х - удалить) -
при этом у элемента selected становится false.
2-й компонет отображает объект в виде дерева, у каждого узла слева чекбокс (checked в зависимости от selected).
У узла можно менять статус (checked/unchecked).
Состояние обоих компонент должно быть синхронизировано - все checked в дереве должны отображаться в списке,
в списке не может быть не checked в дереве элементов.
Оба компонента должны отображаться одновременно на странице.
</p>
      </section>
    </footer>
  </div>
</template>


