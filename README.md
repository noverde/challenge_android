Teste Noverde - Android developer
===============	

Este desafio é destinado aos candidatos à vaga de Android developer para avaliação dos quesitos técnicos.

## Objetivo

Neste desafio o objetivo é desenvolver um app que irá solicitar algumas informações de uma pessoa que deseja fazer uma aplicação para um empréstimo na Noverde, enviar a requisição para uma API e exibir o resultado.

## Telas

As imagens de referência para a criação da interface estão localizadas na pasta `images`.

## Pré-requisitos

- As telas devem se adaptar para diferentes tamanhos (não precisa de tratamento para modo landscape, pode fixar modo portrait)
- Não deve permitir solicitar um valor menor do que R$ 500 ou maior que R$ 4000
- Versão mínima do SDK: 16

## Utilização da API

> Para utilizar a API você deverá passar um token de autenticação que será enviado por email e é  exclusivo para uso no desenvolvimento desse desafio.

**URL**: https://api.noverde-hmg.net/fakes
**Method**: POST
**Header**: Authorization: `Bearer yourcustomtoken`
**Request**:
```json
{
"cpf": "99999999999",
"amount": 9999.99
}
```
- **cpf:** CPF informado pelo usuário (somente números);
- **amount:** Valor solicitado pelo usuário em decimal;

**Response**
```json
{
"status": "approved",
"amount": 2500.00,
"period": 8,
"installment": 350.00,
"first_due_date": "2020-12-25"
}
```

- **status:** Poderá ser "approved" ou "denied" (aprovado ou negado);
- **amount:** O valor total do empréstimo aprovado;
- **period:** A quantidade de parcelas a pagar;
- **installment:** O valor da parcela;
- **first_due_date:** A data de vencimento da primeira parcela;

> **Dicas para testar:** 
> - CPFs com final maior que 6 são negados;
> - CPFs com final 0, 1 e 6 são aprovados; 
> - CPFs com final 2, 3, 4 e 5 são aprovados com proposta renegociada;
> - Propostas com valor maior que R$4000 são calculadas sobre R$4000;
> - Propostas com valor final menor que R$500 são negadas;

### Fluxo do Resultado
- Caso a API retorne com status "approved" e o campo amount SEJA IGUAL ao valor solicitado pelo usuário, você deverá exibir os detalhes do empréstimo conforme o arquivo **tela_04.png**.
- Caso a API retorne com status "approved" e o campo amount SEJA MENOR que o valor solicitado pelo usuário, você deverá exibir os detalhes do empréstimo porém sequir o arquivo **tela_05.png**.
- Caso a API retorne com status "denied", você deve exibir conforme o arquivo **tela_06.png**.

## (Bônus) - Persistência do resultado
Quando a solicitação for aprovada, o aplicativo deve persistir o resultado para que ao abrir o app novamente não permita fazer uma nova solicitação, mas sim seja exibida a tela de aprovação.

## Execução e entrega
Você deve enviar o código em um repositório GIT de sua preferência. Adicione um arquivo README.md com os procedimentos para executar o projeto. Pedimos que trabalhe sozinho e não divulgue o resultado na internet.

### O que será avaliado?
- Técnicas utilizadas para resolver o problema;
- Layouts adaptáveis e de acordo com os arquivos de exemplo;
- Legibilidade;
- Arquitetura utilizada;
- Boas práticas.
