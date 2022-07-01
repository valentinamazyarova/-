# Кнвадратный метр
Учебный SPA проект магазина по продаже недвижимости, реализован на нативном JavaScript
## Описание
* При открыти магазины мы попадаем на главную страницу, на которой отборажены фильтр и карточки товаров.
* Информация от товарах и информация для фильтра хранится в стороннем API, который был предоставлен в учебных целях студентам школы webcademy.
* Получаемые с сервера данные хранятся в общем объекте state
* В проекте была реализована маршрутизация. С помощью прослушки события "hashchange" запускается функция router 
```js
//Router
const routes = [
    { path: '/', component: homePage },
    { path: 'item', component: singleItem },
    { path: 'favourites', component: favoritePage },
    { path: 'bids', component: bidsPage }
];
  // Поиск компонента в Маршрутах на основании запроса
function findComponentByPath(path, routes){
    return routes.find(function(route){
        return route.path === path;
    });
}

// Функция Роутер
function router () {
    // Split path to array
    const pathArray = location.hash.split('/');

    // Set current path
    let currentPath = pathArray[0] === '' ? '/' : pathArray[1];
    currentPath = currentPath === '' ? '/' : currentPath; // item // bids

    state.routeParams = pathArray[2] ? pathArray[2] : ''

    // Выбираем компонент для указанного адреса, либо компонент с ошибкой
    const { component = errorPage } = findComponentByPath(currentPath, routes) || {};

    // Отображение компонента на старнице 
    component(state);

}

// Прослушка событий и запуск роутера
window.addEventListener('load', router);
window.addEventListener('hashchange', router);
```
* Приложение было разделено по компонентам с применением паттерна MVC.
* Приложение имеет возможность оставлять заявку на преобретение недвижимости, также можно добавлять в избранное, понравившиеся объекты.

#### Ссылка на GitHub Pages: https://valentinamazyarova.github.io/Kvadtatnay-metr/
#### Посмотреть код: https://github.com/valentinamazyarova/Kvadratny-metr-dev.git
Инструкции по запуску dev версии проекта: 
```
   git clone https://github.com/valentinamazyarova/Kvadratny-metr-dev.git
   cd Kvadratny-metr-dev
   npm i
   npm run start
```


