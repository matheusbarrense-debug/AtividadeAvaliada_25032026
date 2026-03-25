# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: *Preencha aqui*  
RA: *Preencha aqui*  
Data: *Preencha aqui*  

---

# 1. Definição do MVP
Descreva aqui **qual parte do sistema** foi incluída no seu MVP.  
Explique claramente:

- O que está **dentro** do MVP  
- O que está **fora** do MVP  
- Por que você fez essas escolhas  

Exemplo de início:  
> “Meu MVP cobre o processo de venda desde a identificação/cadastro do cliente até a emissão do comprovante, incluindo tratamento de estoque insuficiente.”

---

# 2. Regras de Negócio (mínimo: 5)
Liste e descreva **cada RN** de forma clara.

**RN01 —**  
**RN02 —**  
**RN03 —**  
**RN04 —**  
**RN05 —**  

(Adicione mais se quiser.)

---

# 3. Requisitos Funcionais (mínimo: 8)
Liste os requisitos funcionais do seu MVP.

**RF01 —**  
**RF02 —**  
**RF03 —**  
**RF04 —**  
**RF05 —**  
**RF06 —**  
**RF07 —**  
**RF08 —**  

(Adicione mais se quiser.)

---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 —**  
**RNF02 —**  
**RNF03 —**  
**RNF04 —**  

(Adicione mais se quiser.)

---

# 5. Casos de Uso (mínimo: 10)
### Inserir **diagrama de casos de uso geral**, demonstrando claramente:
- os 10 casos
- relação entre eles e atores
- pelo menos 3 includes
- pelo menos 3 extends

---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---
## **UC01 — Realizar Venda de Balcão**

**Ator(es):** Atendente. **Descrição:** Permite ao atendente registrar itens solicitados pelo cliente, calcular o total e processar o pagamento. **Pré-condições:** Usuário autenticado; Produto devidamente cadastrado. **Pós-condições:** Venda registrada; Estoque atualizado (RF07); Comprovante emitido (RF05).

### Fluxo Principal

1. O atendente inicia uma nova venda.
    
2. O atendente busca o produto (Include: UC02).
    
3. O atendente informa a quantidade desejada.
    
4. O sistema valida se há estoque disponível (RN01).
    
5. O sistema adiciona o item ao carrinho e atualiza o total parcial.
    
6. O atendente finaliza a venda selecionando a forma de pagamento (Dinheiro ou Cartão).
    
7. O sistema gera o comprovante e abate os itens do estoque.
    

### Fluxos Alternativos / Exceções

- **FA01 — Estoque Insuficiente:** Se a quantidade for maior que o estoque, o sistema bloqueia a inserção e exibe um alerta.
    
- **FA02 — Venda a Prazo:** Se o pagamento for a prazo, inicia-se o Extend: UC04.
    

### Relacionamentos

- **Include:** UC02 — Pesquisar Produto.
    
- **Extend:** UC04 — Finalizar Venda a Prazo.
    

---

## **UC02 — Pesquisar Produto**

**Ator(es):** Atendente, Gerente, Farmacêutico. **Descrição:** Consultar a existência, preço e nível de estoque de um item no sistema (RF01/RF04). **Pré-condições:** Acesso ao módulo de busca. **Pós-condições:** Dados do produto exibidos na tela.

### Fluxo Principal

1. O usuário insere o nome, código de barras ou fabricante do item.
    
2. O sistema consulta a base de dados centralizada (RNF01).
    
3. O sistema retorna a descrição, preço unitário e saldo em estoque.
    

### Fluxos Alternativos / Exceções

- **FA01 — Produto Não Encontrado:** O sistema sugere uma busca por termos similares ou informa que o item não consta no catálogo.
    

### Relacionamentos

- **Include:** (Nenhum)
    

---

## **UC03 — Cadastrar Cliente**

**Ator(es):** Atendente. **Descrição:** Registro rápido de novos clientes para permitir histórico de compras ou vendas a prazo (RF03). **Pré-condições:** CPF em mãos. **Pós-condições:** Cliente habilitado para compras no sistema.

### Fluxo Principal

1. O atendente acessa o formulário de cadastro rápido.
    
2. O atendente insere Nome, CPF e Contato.
    
3. O sistema valida se o CPF já existe na base.
    
4. O sistema salva o registro.
    

### Fluxos Alternativos / Exceções

- **FA01 — CPF Inválido:** O sistema alerta o erro e solicita correção.
    

### Relacionamentos

- **Include:** (Nenhum)
    

---

## **UC04 — Finalizar Venda a Prazo**

**Ator(es):** Atendente. **Descrição:** Vincula a venda ao CPF do cliente para cobrança posterior (RF06). **Pré-condições:** Cliente previamente cadastrado (UC03); Venda em andamento. **Pós-condições:** Título gerado em Contas a Receber.

### Fluxo Principal

1. O atendente seleciona "Venda a Prazo" como método de pagamento.
    
2. O atendente identifica o cliente pelo CPF (RN03).
    
3. O sistema verifica se o cliente possui restrições ou dívidas atrasadas (RN11).
    
4. O sistema confirma a transação e agenda a data de vencimento.
    

### Fluxos Alternativos / Exceções

- **FA01 — Limite de Crédito/Atraso:** Se o cliente possuir títulos "Atrasados", o sistema bloqueia a venda conforme RN11.
    

### Relacionamentos

- **Extend:** UC01 — Realizar Venda de Balcão.
    

---

## **UC05 — Registrar Entrada de Mercadoria**

**Ator(es):** Gerente / Administrativo. **Descrição:** Atualiza o estoque físico e gera obrigações financeiras a partir de uma nota fiscal de fornecedor (RF11). **Pré-condições:** Produto cadastrado; Nota fiscal do fornecedor disponível. **Pós-condições:** Estoque incrementado; Lançamento em Contas a Pagar realizado (RN07).

### Fluxo Principal

1. O usuário acessa o módulo de Compras.
    
2. O usuário informa o fornecedor e os itens recebidos.
    
3. O usuário insere as quantidades e valores de custo.
    
4. O sistema atualiza o saldo de estoque físico (RN06).
    
5. O sistema gera automaticamente um título no Contas a Pagar.
    

### Fluxos Alternativos / Exceções

- **FA01 — Divergência na Conferência:** O usuário suspende a entrada até que os itens físicos coincidam com a nota.
    

### Relacionamentos

- **Include:** UC07 — Gerenciar Contas a Pagar.
    

---

## **UC06 — Processar Devolução de Item**

**Ator(es):** Atendente / Gerente. **Descrição:** Estorno de uma venda e retorno do produto ao estoque disponível (RF08). **Pré-condições:** Apresentação do comprovante original (RN10). **Pós-condições:** Estoque retificado; Ajuste financeiro concluído.

### Fluxo Principal

1. O usuário informa o número do comprovante da venda original.
    
2. O sistema localiza os itens vendidos.
    
3. O usuário seleciona quais itens serão devolvidos.
    
4. O sistema estorna o valor (ou gera crédito) e devolve a unidade ao estoque (RF07).
    

### Fluxos Alternativos / Exceções

- **FA01 — Comprovante Inexistente:** O sistema recusa o procedimento sem a validação da venda original.
    

---

## **UC07 — Gerenciar Contas a Pagar**

**Ator(es):** Financeiro. **Descrição:** Controle de dívidas com fornecedores e despesas da unidade (RF13). **Pré-condições:** Título lançado no sistema. **Pós-condições:** Status do título atualizado para "Paga".

### Fluxo Principal

1. O usuário consulta os títulos com vencimento para a data atual.
    
2. O usuário confirma o pagamento do título junto ao banco.
    
3. O usuário registra a data de pagamento e o valor final no sistema.
    
4. O sistema altera o status para "Paga".
    

### Fluxos Alternativos / Exceções

- **FA01 — Cancelamento de Título:** O usuário cancela um título inserindo uma justificativa obrigatória (RN12).
    

---

## **UC08 — Gerenciar Contas a Receber**

**Ator(es):** Financeiro / Atendente. **Descrição:** Monitoramento e baixa de pagamentos de vendas a prazo (RF12). **Pré-condições:** Existência de vendas a prazo finalizadas. **Pós-condições:** Baixa financeira no sistema.

### Fluxo Principal

1. O usuário busca títulos por CPF do cliente ou data de vencimento.
    
2. O sistema destaca títulos com status "Atrasada" (RN05).
    
3. O cliente efetua o pagamento.
    
4. O usuário realiza a baixa do título, alterando para "Recebida".
    

---

## **UC09 — Atualizar Preço de Produto**

**Ator(es):** Gerente / Administrador. **Descrição:** Permite alterar o preço de venda de itens no catálogo (RN04). **Pré-condições:** Usuário com perfil de Gerente ou Administrador. **Pós-condições:** Novos preços refletidos instantaneamente no balcão.

### Fluxo Principal

1. O Gerente busca o produto desejado.
    
2. O Gerente insere o novo valor de venda.
    
3. O sistema valida as permissões de acesso (RNF04).
    
4. O sistema salva a alteração e registra o log de quem alterou.
    

---

## **UC10 — Registrar Perda de Mercadoria**

**Ator(es):** Gerente / Farmacêutico. **Descrição:** Retirada de itens do estoque por vencimento ou dano (RF09). **Pré-condições:** Identificação física do item avariado/vencido. **Pós-condições:** Estoque atualizado; Relatório de perdas alimentado.

### Fluxo Principal

1. O usuário seleciona o produto e a quantidade perdida.
    
2. O usuário informa o motivo (Vencimento, Quebra, Roubo).
    
3. O sistema remove os itens do saldo disponível para venda.
    
4. O sistema gera um alerta se o estoque atingir o nível mínimo (RF14). 



---

> Repita essa estrutura para **todos os seus casos de uso** (mínimo 10).


