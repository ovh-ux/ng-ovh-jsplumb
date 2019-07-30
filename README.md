# ng-ovh-jsplumb

> Allow to draw links between elements using [jsplumb toolkit](http://www.jsplumb.org/).

[![Downloads](https://badgen.net/npm/dt/@ovh-ux/ng-ovh-jsplumb)](https://npmjs.com/package/@ovh-ux/ng-ovh-jsplumb) [![Dependencies](https://badgen.net/david/dep/ovh-ux/ng-ovh-jsplumb)](https://npmjs.com/package/@ovh-ux/ng-ovh-jsplumb?activeTab=dependencies) [![Dev Dependencies](https://badgen.net/david/dev/ovh-ux/ng-ovh-jsplumb)](https://npmjs.com/package/@ovh-ux/ng-ovh-jsplumb?activeTab=dependencies) [![Gitter](https://badgen.net/badge/gitter/ovh-ux/blue?icon=gitter)](https://gitter.im/ovh/ux)

## Install

```sh
yarn add @ovh-ux/ng-ovh-jsplumb
```

## Usage

```js
import angular from 'angular';
import ngOvhJsplumb from '@ovh-ux/ng-ovh-jsplumb';

angular
  .module('myApp', [
    ngOvhJsplumb,
  ]);
```

For jQuery UI, we only need draggable and droppable functionalities (and the few core functionalities). So we can load only these files.

### Example

First, make sure `jsplumb` is ready by calling `jsPlumbService.jsplumbInit` method:

```js
import angular from 'angular';

angular
  .module('myApp')
  .controller('MyController', class {
    /* @ngInject */
    constructor($scope, jsPlumbService) {
      this.$scope = $scope;
      this.jsPlumbService = jsPlumbService;
    }

    $onInit() {
      this.$scope.jsplumbReady = false;

      this.jsPlumbService
        .jsplumbInit()
        .finally(() => {
          this.$scope.jsplumbReady = true;
        });
    }
  });
```

Create an instance of `ng-ovh-jsplumb` with the `jsplumbInstance` directive:

```html
<div
    data-ng-if="jsplumbReady"
    data-jsplumb-instance>
    …
</div>
```

## Related

- [jsPlumb](http://jsplumb.org)
- [jQuery UI](http://jqueryui.com/) as a dependency of jsPlumb.

## Test

```sh
yarn test
```

## Contributing

Always feel free to help out! Whether it's [filing bugs and feature requests](https://github.com/ovh-ux/ng-ovh-jsplumb/issues/new) or working on some of the [open issues](https://github.com/ovh-ux/ng-ovh-jsplumb/issues), our [contributing guide](CONTRIBUTING.md) will help get you started.

## License

[BSD-3-Clause](LICENSE) © OVH SAS
