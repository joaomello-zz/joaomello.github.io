---
published: true
title: Angular bindToController
layout: post
tags: [angular, directive, frontend]
categories: [webdev]
---
Na versão 1.2 do Angular foi introduzido a sintax *controllerAs*, remvendo a necessidade de usar *$scope* (não em todos os casos). Mas, mesmo assim quando criavamos nossa diretiva usando *controllerAs* tinhamos que usar *$scope* para poder acessar as propriedades passadas a ela, segue o exemplo?

```JavaScript
angular
    .module('app', [])
    .directive('minhaDiretiva', minhaDiretiva);

function minhaDiretiva() {
    return {
        restrict: 'E',
        scope: {
            contador: '='
        },
        controller: function ($scope) {
            this.add = function () {
                ++$scope.contador;
            };
        },
        controllerAs: 'vm',
        template: ' <div> ' +
        '   <input ng-model="contador"> ' +
        '   <button type="button" ng-click="vm.add()">Add</button> ' +
        '</div>'
    };
}
```

Percebe-se que fica não fica nice assim, na versão 1.3 do angular ficou melhor:
```js
angular
	.module('app', [])
	.directive('minhaDiretiva', minhaDiretiva);

```
Muito melhor, não? Você pode passar para o *bindToController* os parâmetros que deseja, ou apenas passar *true* que ele fara para todas as propriedades declaradas no scope, em toda diretiva que criar um novo escopo.