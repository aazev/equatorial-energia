<div id="topo"></div>

<div align="center">
    <a style="text-decoration: none" href="https://www.equatorialenergia.com.br/">
        <img src="https://play-lh.googleusercontent.com/tiksHECQh6MNAZHmW45xO38h8hJSLXYx7c5SrfzyMAvjcTQQX5Qt8XBSFV3xI4S0el3Q" alt="icone equatorial energia" width="auto" height="95" />
    </a>
</div>

<h3 align="center">Equatorial Energia - Api</h3>

A Equatorial Energia é uma holding que controla as distribuidoras de energia Equatorial Energia Alagoas, Equatorial Energia Maranhão, Equatorial Energia Pará, Equatorial Energia Piauí, CEEE Equatorial Energia e CEA Equatorial Energia.

## Sobre

Um modulo TypeScript que permite interagir facilmente com a API [Equatorial Energia](https://www.equatorialenergia.com.br/).

-   Orientado a objecto
-   Performático

Nesse módulo, está disponível para uso os seguintes estados:

-   [Alagoas](https://al.equatorialenergia.com.br/)
-   [Maranhão](https://ma.equatorialenergia.com.br/)
-   [Pará](https://pa.equatorialenergia.com.br/)
-   [Piauí](https://pi.equatorialenergia.com.br/)

## Instalação

-   npm

```sh
npm install equatorial-energia
```

-   yarn

```sh
yarn add equatorial-energia
```

## Exemplo de uso

```js
import { Client } from "equatorial-energia";

const clien = new Client("username", "birhtday", {
    state: "PI",
});

client
    .loginWithBirhtday()
    .then((structure) => {
        client
            .listInvoice(structure.getContractsId()[0], structure.getToken())
            .then(console.log)
            .catch(console.log);
    })
    .catch(console.log);
```

ou

```js
const { Client } = require("equatorial-energia");

const client = new Client("username", "birhtday", {
    state: "PI",
});

client
    .loginWithBirhtday()
    .then((structure) => {
        client
            .listInvoice(structure.getContractsId()[0], structure.getToken())
            .then(console.log)
            .catch(console.log);
    })
    .catch(console.log);
```

Uma vez instanciado o client, pode ser usado conjunto de ferramentas disponíveis

## Toolset

**Observação** Observe que cada funcionalidade abaixo se refere a class `Client`

-   Client.loginWithBirhtday(cpf?: `string`, birthday?: `string`): `Promise<StructureAccessToken>` - autentica usuário na plataforma com cpf e data de nascimento

    ```js
    client.loginWithBirhtday("00000000000", "13/01/2022");
    ```

-   Client.loginWithDocument(cpf?: `string`, document?: `string`): `Promise<StructureAccessToken>` - autentica usuário na plataforma com cpf e primeiros dígitos do RG

    ```js
    client.loginWithDocument("00000000000", "000");
    ```

-   Client.loginWithCnpj(cnpj?: `string`, email?: `string`): `Promise<StructureAccessToken>` - autentica usuário na plataforma com cnpj e o email cadastrado

    ```js
    client.loginWithCnpj("00000000000000", "email@elizandrodantas.com");
    ```

-   Client.loginWithMontherName(cpf?: `string`, monther?: `string`): `Promise<StructureAccessToken>` - autentica usuário na plataforma com cpf e nome da mãe

    ```js
    client.loginWithMontherName("00000000000", "Monther Name");
    ```

-   Client.listInvoice(contract: `string`, token?: `string`): `Promise<InvoiceList>` - lista ultimas faturas

    -   `token`: caso não passado o parâmetro, ele ira buscar por token dentro da instância

    ```js
    client.listInvoice("000000000", "JWT");
    ```

-   Client.openInvoices(contract: `string`): `Promise<InvoiceOpen>` - lista fatura não pagas

    -   Login não obrigatório;

    ```js
    client.openInvoices("0000000000");
    ```

-   Client.consumpitonHistory(contract: `string`, token?: `string`): `Promise<InvoiceHistory>` - detalhes de consumo na sua fatura como:

    1.  consumo de kwh da fatura;
    2.  tributos.

    -   `token`: caso não passado o parâmetro, ele ira buscar por token dentro da instância

    ```js
    client.consumpitonHistory("0000000000", "JWT");
    ```

-   Client.installationDetails(contract: `string`): `Promise<InstallationDetails>` - detalhes da instalação e situação do contrato

    -   Login não obrigatorio;

    ```js
    client.installationDetails("0000000000");
    ```

## Contato

Email: dantaspm@icloud.com
