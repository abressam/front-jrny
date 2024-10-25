<div>
  <h1>Padrões de Projeto e Multicamadas<br>Trabalho Final</h1>
</div>

<div>
  <h3>Autor: Amanda Bressam Martins</h3>
</div>

# Relatório

## Padrão de Projeto 1: Factory Pattern

`Melhoria: remover repetição de código`
   
Esse padrão foi considerado para retirar a ***repetição de código***. Vejamos o exemplo presente no arquivo `upload.service.ts`

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

