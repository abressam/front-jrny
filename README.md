<div>
  <h1>Padrões de Projeto e Multicamadas<br>Trabalho Final</h1>
</div>

<div>
  <h3>Autor: Amanda Bressam Martins</h3>
</div>

# Relatório

## Melhoria 1: Remover repetição de código

> [!NOTE]
> Padrão de projeto escolhido: **Factory Pattern**

Vejamos o exemplo presente no arquivo `upload.service.ts`

Possuímos repetição dos headers e de variáveis que tem seus valores atribuídos a partir do local storage:

![msg2](https://github.com/user-attachments/assets/b0d80df4-13a6-4ca0-8179-25b24e6978a1)

Portanto, podemos encapsular a lógica dos headers em uma classe separada, assim como as variáveis mais utilizadas:

`HttpOptionsFactory`

![image](https://github.com/user-attachments/assets/14b7e5c5-9bb6-4bfd-8a7f-8188ffa76ad8)

`ConfigService`

![image](https://github.com/user-attachments/assets/4dddbc2d-e4d6-4bd8-b2a5-29c111614d3f)

Dessa maneira, o **comportamento** das classes **não é alterado** e se torna mais ***legível e organizado***, facilitando ***manutenções futuras***.
* Criação da variável `baseUrl`
* Adição das classes HttpOptionsFactory e ConfigService ao construtor
* Utilização das novas classes nos métodos

![image](https://github.com/user-attachments/assets/1294e479-8fec-4b70-bfdc-d66e6d1d5f8a)

## Melhoria 2: Abstrair a complexidade da comunicação de serviços no componente

> [!NOTE]
> Padrão de projeto escolhido: **Facade Pattern**

Analisaremos o seguinte arquivo: `create-project.component.ts`

Esse componente lida com o `uploadService`, fazendo as operações de **uploadFile**, **deleteFile**, e **updateFile** e o `accountService` para a operação **LoggedIn**

![msg3](https://github.com/user-attachments/assets/35f67550-dd43-475c-8bbc-601b1acb5728)

![msg5](https://github.com/user-attachments/assets/43850bd2-79c9-45c3-83bc-db8a469dbf9f)

![msg4](https://github.com/user-attachments/assets/a35e44ae-345a-474f-8a48-fcc46730a4af)

Portanto, podemos criar um serviço de "fachada" (Facade) para fazer essa separação:

Criar o arquivo `project-facade.service.ts`

Aproveitando para também adicionar as seguintes funções: convertFileToBase64, navigateToProfile, navigateToSignIn e handleHttpError

![image](https://github.com/user-attachments/assets/ae6926f3-0209-413f-b306-9fc54cb26fb4)

![image](https://github.com/user-attachments/assets/3a28a027-f14d-4650-ab23-0656fab22a1f)

Assim, separamos os serviços e operações que o `create-project.component.ts` precisa. Então, ao utilizar o padrão, ficaria da seguinte forma:

![msg6](https://github.com/user-attachments/assets/f2786d8d-e15c-47f1-b754-dfc8441b338d)

![msg7](https://github.com/user-attachments/assets/d039fdaf-75fd-490f-9bb1-9d8f1b06aaa3)

![msg8](https://github.com/user-attachments/assets/671d20ed-c8ec-489c-98eb-2e7a78db0bcc)

Com isso, o componente fica **mais simples**, possuindo menos responsabilidades.

## Melhoria 3: ...

> [!NOTE]
> Padrão de projeto escolhido: **...**




