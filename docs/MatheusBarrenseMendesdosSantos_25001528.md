# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: *Matheus Barrense Mendes dos Santos*  
RA: *25001528*  
Data: *25/03/2026*  

---

# 1. Definição do MVP
Descreva aqui **qual parte do sistema** foi incluída no seu MVP.  
Explique claramente:

- O que está **dentro** do MVP  
- O que está **fora** do MVP  
- Por que você fez essas escolhas  

Meu MVP cobre o processo de atendimento com o admnistrativo, permitindo um controle de vendas que evite estoques fantasmas dentro do sistema e finanças desencontradas, o serviço de atendimento agora ligado com o sistema é capaz de registrar as compras dos clientes em tempo real e impedir que a farmácia sofra de falta de estoque, o que está fora de meu MVP é acesso aos gastos de manutenção do estabelicmento, a validação de receitas médicas controladas e fiz essas escolhas vizando a eficiência e fluidez do sistema

Exemplo de início:  
> “Meu MVP cobre o processo de venda desde a identificação/cadastro do cliente até a emissão do comprovante, incluindo tratamento de estoque insuficiente.”

---

# 2. Regras de Negócio (mínimo: 5)
Liste e descreva **cada RN** de forma clara.

**RN01 —** Bloqueio de Venda sem Estoque: Não é permitida a venda de produtos cuja quantidade em estoque seja zero.
**RN02 —** Venda de Controlados: Medicamentos que exigem retenção de receita só podem ser finalizados após validação do perfil "Farmacêutico".
**RN03 —** Histórico de Clientes: Toda venda a prazo deve, obrigatoriamente, estar vinculada a um CPF cadastrado.
**RN04 —** Atualização de Preços: Somente usuários com perfil de "Gerente" ou "Administrador" podem alterar o preço de venda de um produto.
**RN05 —** Status de Cobrança: Títulos não pagos após a data de vencimento devem ter o status alterado automaticamente para "Atrasada".
**RN06 —** Entrada de Mercadoria: Uma compra de fornecedor só é considerada concluída após a conferência e entrada física no estoque.
**RN07 —** Registro de Contas a Pagar: Toda nota fiscal de compra emitida contra a farmácia deve gerar obrigatoriamente um lançamento em contas a pagar.
**RN08 —** Unidade de Medida: Todo produto deve possuir uma unidade de medida definida (ex: caixa, frasco, comprimido) no cadastro.
**RN09 —** Campos Obrigatórios: O cadastro de produtos exige: Descrição, Preço, Unidade, Fabricante e Nível Mínimo de Estoque.
**RN10 —** Devolução de Itens: A devolução de um produto exige a apresentação do comprovante da venda original.
**RN11 —** Limite de Crédito: Vendas a prazo podem ser bloqueadas se o cliente possuir títulos com status "Atrasada" (conforme política da matriz).
**RN12 —** Transparência Financeira: Lançamentos em "Contas a Pagar" não podem ser excluídos, apenas cancelados com justificativa registrada.

(Adicione mais se quiser.)

---

# 3. Requisitos Funcionais (mínimo: 8)
Liste os requisitos funcionais do seu MVP.

**RF01 —** Pesquisa de Produtos: O sistema deve permitir a busca de itens por nome, código de barras ou fabricante.
**RF02 —** Registro de Venda: O sistema deve realizar a baixa de itens e gerar o total da venda no balcão.
**RF03 —** Cadastro de Clientes: O sistema deve permitir o registro rápido de dados pessoais de novos clientes.
**RF04 —** Verificação de Estoque: O sistema deve consultar a disponibilidade do item em tempo real antes de concluir a venda.
**RF05 —** Emissão de Comprovante: O sistema deve gerar e imprimir um comprovante detalhado após cada operação de venda.
**RF06 —** Gestão de Vendas a Prazo: O sistema deve permitir vincular uma venda ao cadastro do cliente para pagamento posterior.
**RF07 —** Atualização Automática de Estoque: O sistema deve debitar ou creditar produtos do inventário após vendas, devoluções, perdas ou compras.
**RF08 —** Registro de Devoluções: O sistema deve permitir o estorno de itens vendidos e o ajuste financeiro correspondente.
**RF09 —** Controle de Perdas: O sistema deve permitir o registro de produtos vencidos ou danificados, removendo-os do estoque disponível.
**RF10 —** Transferência entre Unidades: O sistema deve permitir a movimentação de produtos de uma farmácia para outra da rede.
**RF11 —** Gestão de Compras: O sistema deve registrar a entrada de mercadorias enviadas por fornecedores.
**RF12 —** Gestão de Contas a Receber: O sistema deve listar e controlar vencimentos de vendas feitas a prazo.
**RF13 —** Gestão de Contas a Pagar: O sistema deve registrar dívidas com fornecedores e despesas fixas da unidade.
**RF14 —** Alerta de Estoque Mínimo: O sistema deve disparar notificações quando um produto atingir o nível crítico de reposição.
**RF15 —** Relatório de Mais Vendidos: O sistema deve gerar rankings de produtos por volume de saída e rentabilidade.
**RF16 —** Relatório Financeiro: O sistema deve consolidar lançamentos de entradas e saídas por período (dia/semana/mês).
**RF17 —** Relatório de Inatividade: O sistema deve listar produtos que não tiveram movimentação em um período determinado.

(Adicione mais se quiser.)

---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 —** Centralização de Dados: O sistema deve utilizar uma base de dados única e centralizada para integração entre as unidades.
**RNF02 —** Desempenho de Busca: As consultas de produtos no balcão devem retornar resultados em menos de 2 segundos.
**RNF03 —** Disponibilidade: O sistema deve estar disponível para operação 99,9% do tempo durante o horário comercial.
**RNF04 —** Segurança de Acesso: O sistema deve exigir autenticação (usuário e senha) com diferentes níveis de permissão (RBAC).
**RNF05 —** Interface Intuitiva: O módulo de vendas deve ser otimizado para operação rápida via teclado e leitor de código de barras.
**RNF06 —** Integridade de Dados: O sistema deve garantir que uma venda não ocorra simultaneamente com uma baixa de estoque manual do mesmo item (concorrência).
**RNF07 —** Backup Automático: O sistema deve realizar cópias de segurança dos dados diariamente na nuvem.
**RNF08 —** Escalabilidade: A arquitetura deve suportar a adição de novas unidades de farmácia sem perda de performance.
**RNF09 —** Compatibilidade de Hardware: O sistema deve ser compatível com impressoras térmicas e leitores de código de barras USB/Bluetooth.
**RNF10 —** Auditoria: Todas as senhas de usuários devem ser armazenadas com criptografia (hashing).
**RNF11 —** Tempo de Resposta Financeiro: Relatórios complexos (ex: anual) não devem demorar mais de 30 segundos para serem gerados.
**RNF12 —** Padronização: A interface deve seguir um padrão visual único em todos os módulos (Financeiro, Estoque, Vendas).
**RNF13 —** Recuperação de Desastres: Em caso de falha crítica, o sistema deve permitir a recuperação total dos dados em no máximo 4 horas.
**RNF14 —** Suporte Multi-Plataforma: O sistema administrativo (matriz) deve ser acessível via navegadores web (Chrome, Firefox, Edge).

(Adicione mais se quiser.)

---

# 5. Casos de Uso (mínimo: 10)
### Inserir **diagrama de casos de uso geral**, demonstrando claramente:
- os 10 casos
- relação entre eles e atores
- pelo menos 3 includes
- pelo menos 3 extends
<img width="1879" height="1008" alt="image" src="https://github.com/user-attachments/assets/3f897e43-50c6-478e-9992-fe2ee07a88f8" />

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
    
<img width="622" height="619" alt="image" src="https://github.com/user-attachments/assets/87f1f906-068e-4545-ad5b-9814c46c2db4" />

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
    
<img width="679" height="374" alt="image" src="https://github.com/user-attachments/assets/e6c5ceb3-a9aa-4151-a310-16819725e56a" />

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
    
<img width="565" height="432" alt="image" src="https://github.com/user-attachments/assets/ff97fe42-db73-426b-8e5a-2ec5890caad0" />

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
    
<img width="654" height="432" alt="image" src="https://github.com/user-attachments/assets/4ecdb9aa-b9d7-43fe-b142-fea3bd870774" />

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
    
<img width="621" height="343" alt="image" src="https://github.com/user-attachments/assets/f190c018-a645-4a15-8a34-d5a51376298c" />

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
    
<img width="697" height="432" alt="image" src="https://github.com/user-attachments/assets/e41138fe-04f7-4cb4-882d-b365d5c22d35" />

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
<img width="565" height="357" alt="image" src="https://github.com/user-attachments/assets/c90f957f-9302-4ba1-ab37-fd9614c582bf" />

---

## **UC08 — Gerenciar Contas a Receber**

**Ator(es):** Financeiro / Atendente. **Descrição:** Monitoramento e baixa de pagamentos de vendas a prazo (RF12). **Pré-condições:** Existência de vendas a prazo finalizadas. **Pós-condições:** Baixa financeira no sistema.

### Fluxo Principal

1. O usuário busca títulos por CPF do cliente ou data de vencimento.
    
2. O sistema destaca títulos com status "Atrasada" (RN05).
    
3. O cliente efetua o pagamento.
    
4. O usuário realiza a baixa do título, alterando para "Recebida".
    
<img width="587" height="328" alt="image" src="https://github.com/user-attachments/assets/77b5206e-6a1d-482f-a3e8-52269f194020" />

---

## **UC09 — Atualizar Preço de Produto**

**Ator(es):** Gerente / Administrador. **Descrição:** Permite alterar o preço de venda de itens no catálogo (RN04). **Pré-condições:** Usuário com perfil de Gerente ou Administrador. **Pós-condições:** Novos preços refletidos instantaneamente no balcão.

### Fluxo Principal

1. O Gerente busca o produto desejado.
    
2. O Gerente insere o novo valor de venda.
    
3. O sistema valida as permissões de acesso (RNF04).
    
4. O sistema salva a alteração e registra o log de quem alterou.
    
<img width="613" height="432" alt="image" src="https://github.com/user-attachments/assets/1dbb84b8-0d16-40ce-9ed3-fc43fa62f71f" />

---

## **UC10 — Registrar Perda de Mercadoria**

**Ator(es):** Gerente / Farmacêutico. **Descrição:** Retirada de itens do estoque por vencimento ou dano (RF09). **Pré-condições:** Identificação física do item avariado/vencido. **Pós-condições:** Estoque atualizado; Relatório de perdas alimentado.

### Fluxo Principal

1. O usuário seleciona o produto e a quantidade perdida.
    
2. O usuário informa o motivo (Vencimento, Quebra, Roubo).
    
3. O sistema remove os itens do saldo disponível para venda.
    
4. O sistema gera um alerta se o estoque atingir o nível mínimo (RF14). 

<img width="697" height="359" alt="image" src="https://github.com/user-attachments/assets/5fcf8d2f-45ae-49ac-ad3d-a14adf1a6931" />


---

> Repita essa estrutura para **todos os seus casos de uso** (mínimo 10).


