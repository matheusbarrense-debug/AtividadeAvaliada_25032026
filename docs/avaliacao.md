# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: *Matheus Barrense Mendes dos Santos*  
RA: *22001528*  
Data: *25/03/2026*  

---

# 1. Definição do MVP
Descreva aqui **qual parte do sistema** foi incluída no seu MVP.  
Explique claramente:
Meu MVP cobre o processo de atendimento com o admnistrativo, permitindo um controle de vendas que evite estoques fantasmas dentro do sistema e finanças desencontradas, o serviço de atendimento agora ligado com o sistema é capaz de registrar as compras dos clientes em tempo real e impedir que a farmácia sofra de falta de estoque, o que está fora de meu MVP é acesso aos gastos de manutenção do estabelicmento, a validação de receitas médicas controladas e fiz essas escolhas vizando a eficiência e fluidez do sistema

- O que está **dentro** do MVP  
- O que está **fora** do MVP  
- Por que você fez essas escolhas  

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

---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---

## **UCXX — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

> Repita essa estrutura para **todos os seus casos de uso** (mínimo 10).


