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

## Melhoria 3: Criar parâmetros de forma modular

> [!NOTE]
> Padrão de projeto escolhido: **Builder**

Para esse caso, temos a seguinte situação no arquivo `curriculum.service.ts`:

![image](https://github.com/user-attachments/assets/c6a7956f-c063-44d4-9bfc-1f42cb49f5b5)

Para isso, podemos contruir a classe ParamsBuilder para facilitar a criação das instâncias de HttpParams

![image](https://github.com/user-attachments/assets/135d8e28-aecc-47f1-94bc-64d624b23c1b)

Então, deixamos o `curriculum.service.ts` da seguinte forma:

![msg9](https://github.com/user-attachments/assets/6fd6cc70-3c86-4749-be0b-7bce207eca88)

Com essa modificação, deixamos a Params está **isolada**. Se for necessário adicionar/remover parâmetros, é possível fazer isso **sem alterar cada método individualmente**.

## Melhoria 4: Criar a validação de formulário em uma classe separada

> [!NOTE]
> Padrão de projeto escolhido: **Factory Pattern**

Seguindo a mesma ideia de separar responsabilidades, temos o arquivo `user-resume.component.ts`, onde a validação do formulário é feita diretamente no componente:

![msg10](https://github.com/user-attachments/assets/d98a7fd9-d990-446a-b15c-c1f4220b8f7e)

Para isso, vamos criar o arquivo `validation.service.ts` com duas funções, sendo uma para validar campos obrigatórios:

![image](https://github.com/user-attachments/assets/f54f8b5d-6ea5-4964-b91c-916ad7ea346c)

E agora, o arquivo ` resume-form.factory.ts` para a validação de cada campo:

![image](https://github.com/user-attachments/assets/f673b796-e93c-4f17-afd3-717ce9720fa2)

Assim, o componente ficará da seguinte forma:

![msg11](https://github.com/user-attachments/assets/464defcc-3763-413d-9155-02827a7000b5)






