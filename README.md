## react-intl-currency-input

A React component for i18n currency input using [Intl API](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Intl).

### Installation

```sh
$ npm install react-intl-currency-input --save-dev
```

### How to use

```js
import React from "react"
import IntlCurrencyInput from "react-intl-currency-input"

const currencyConfig = {
  locale: "pt-BR",
  formats: {
    number: {
      BRL: {
        style: "currency",
        currency: "BRL",
        minimumFractionDigits: 2,
        maximumFractionDigits: 2,
      },
    },
  },
};

const BrlCurrencyComponent = () => {
  const handleChange = (event, value, maskedValue) => {
    event.preventDefault();

    console.log(value); // value without mask (ex: 1234.56)
    console.log(maskedValue); // masked value (ex: R$1234,56)
  };

  return(
    <IntlCurrencyInput currency="BRL" config={currencyConfig}
            onChange={handleChange} />
  );
}

export default BrlCurrencyComponent;

```

### Override currency symbol usage

```js

const BrlCurrencyComponent = () => {
  const handleChange = (event, value, maskedValue) => {
    ...
  };

  return(
    <IntlCurrencyInput 
      currency="ZAR"
      currencySymbolOverride={{"ZAR": "R"}}
      config={currencyConfig}
      onChange={handleChange} />
  );
}

export default BrlCurrencyComponent;

```

### Example

![example](https://cloud.githubusercontent.com/assets/333482/23334967/c7eff3fe-fb80-11e6-870f-be21fe8935ea.gif)

To run the example:

```sh
$ npm run example:start
```

And a new browser window will open at [http://localhost:3000](http://localhost:3000)

### Properties

| Name | Type | Default | Description |
| :---: | :---: | :---: | :--- |
| defaultValue | number | 0 | Sets the default / initial value to be used by the component on the first load |
| currency | string | USD | Sets the [currency code](http://www.xe.com/iso4217.php) |
| currencySymbolOverride | object | null | Sets the override value for the [currency code](http://www.xe.com/iso4217.php) |
| config | object | USD related configuration | Configuration object compliant with react-intl [intlShape](https://github.com/yahoo/react-intl/wiki/API#intlshape) |
| autoFocus | boolean | false | Enables auto-focus when the component gets displayed |
| autoSelect | boolean | false | Enables auto-select when the component gets displayed |
| autoReset | boolean| false | Resets component's internal state when loses focus |
| onChange | function | undefined | `(event, value, maskedValued) => {}`<br><br>Exposes the `Event` itself, the `value` with no mask and `maskedValue` for displaying purposes |
| onFocus | function | undefined | `(event, value, maskedValued) => {`<br><br>Called when the component gains focus |
| onBlur | function | undefined| `(event, value, maskedValued) => {`<br><br>Called when the component loses focus |
| onKeyPress | function| undefined | `(event, key, keyCode) => {}`<br><br>Called when a `key` is pressed |
| max | number| undefined | Maximum value for the input. Input does not change if the value is greater than max |

All the other undocumented properties available for any `React Component` should also be available.

### TO-DO
- [ ] Add unit tests
- [ ] Add a Storybook for examples and UI tests
