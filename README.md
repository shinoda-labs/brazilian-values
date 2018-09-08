# Brazilian Values

[![Build Status](https://travis-ci.org/VitorLuizC/brazilian-values.svg?branch=master)](https://travis-ci.org/VitorLuizC/brazilian-values)

Validates and formats brazilian values, like money (BRL), CPF, CNPJ, dates etc.

## Install

This module is published under NPM registry, so you can install using any Node.js package manager.

```sh
npm install brazilian-values --save-dev

# For Yarn use the command below.
yarn add brazilian-values
```

## Usage

`brazilian-values` provides functions to deal with formatting, validating and parsing brazilian values. All those functions could be imported from package.

```js
import { isCNPJ, formatToCNPJ } from 'brazilian-values';

const value = '12727442000113'

if (!isCNPJ(value))
  throw new Error('CNPJ is not valid.');
const document = formatToCNPJ(value);
//=> '12.727.442/0001-13'
```

## API

### Formatters

#### `formatToBRL`

Formats numbers or texts containing numbers to brazilian currency (BRL).

```js
formatBRL(1928.93)
//=> 'R$ 1.928,93'

formatToBRL('9211928.18203')
//=> 'R$ 9.211.928,18'

formatToBRL(-18.49)
//=> 'R$ -18,49'
```

#### `formatToCEP`

Formats a text containing numbers to CEP.

```js
formatToCEP('15998030')
//=> '15998-030'

formatToCEP('02999')
//=> '02999'
```

#### `formatToCNPJ`

Formats a text containing numbers to CNPJ.

```js
formatToCNPJ('128781')
//=> '12.878.1'

formatToCNPJ('32284981000138')
//=> '32.284.981/0001-38'

formatToCNPJ('00.0.000.00.00--00-00')
//=> '00.000.000/0000-00'
```

#### `formatToCPF`

Formats a text containing numbers to CPF.

```js
formatToCPF('00000000')
//=> '000.000.00'

formatToCPF('00000000000')
//=> '000.000.000-00'

formatToCPF('366.418.768-70')
//=> '366.418.768-70'
```

#### `formatToDate`

Formats a `Date` instance to brazilian formatted date.

```js
formatToDate(new Date(2002, 7, 21))
//=> '21/08/2002'

formatToDate(new Date())
//=> '08/09/2018'
```

#### `formatToPhone`

Formats a text containing numbers to common brazilian phone.

```js
formatToPhone('11')
//=> '(11'

formatToPhone('11971626')
//=> '(11) 9716-26'

formatToPhone('11971626799')
//=> '(11) 9 7162-6799'
```

#### `formatToRG`

Formats a text containing numbers to RG, specifying the state.

> Today, `brazilian-values` supports only **SP** and **RJ** formats.
> Other values are just scaped to input.

```js
formatToRG('00000000A', 'SP')
//=> '00.000.000-A'

formatToRG('00.00.0000-0', 'RJ')
//=> '00.000.000-0'

formatToRG('MG-14.808.688', 'MG')
//=> 'MG-14.808.688'
```

## License

Released under [MIT license](./LICENSE).
