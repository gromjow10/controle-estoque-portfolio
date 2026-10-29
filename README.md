# Controle de Estoque

Aplicação desktop em Python para controlar produtos, entradas, saídas e o valor do estoque pelo custo de compra.

**Autor:** Thiago Dantas  
**Status:** Em desenvolvimento  
**Plataforma:** Windows, com banco de dados local

## Sobre o projeto

Desenvolvo este sistema para aplicar meus estudos de Análise e Desenvolvimento de Sistemas a uma necessidade prática: acompanhar os produtos disponíveis, suas movimentações e os custos do estoque.

O projeto parte de situações do dia a dia de trabalho, como lançamentos incorretos, consulta de documentos e recuperação de dados.

O projeto é construído por etapas, com apoio de IA para orientação, explicações e revisão do código. Implemento e testo as funcionalidades enquanto estudo Python, SQL, interfaces gráficas e controle de versão.

## Funcionalidades implementadas

- Cadastro de produtos com nome, categoria e tipo de medida.
- Edição dos dados dos produtos.
- Exclusão de produtos sem movimentações ou ajustes registrados.
- Pesquisa por nome, sem diferenciar maiúsculas, minúsculas ou acentos.
- Filtro por categoria, combinado com a pesquisa.
- Consulta das quantidades e dos valores disponíveis.
- Entradas com custo unitário de compra e motivo.
- Saídas com motivos predefinidos.
- Bloqueio de retiradas superiores ao saldo disponível.
- Cálculo das saídas pelo custo médio.
- Valor total do estoque, com indicação de custos ainda não informados.
- Ajuste do valor atual do estoque com justificativa.
- Correção do custo de entradas, com recálculo das saídas seguintes.
- Estorno de entradas e saídas, preservando os registros originais.
- Bloqueio de estornos que deixariam o saldo histórico negativo.
- Auditoria de ajustes, correções de custo e estornos.
- Histórico com quantidade, valor, situação e horário de Brasília.
- PDFs opcionais vinculados às entradas e saídas.
- Consulta e abertura dos anexos pelo histórico.
- Exportação conjunta dos PDFs.
- Backup completo em ZIP com banco, anexos e planilha Excel.
- Restauração do banco e dos anexos a partir do backup.
- Cópia de recuperação dos dados atuais antes da restauração.
- Leitura de Excel com prévia dos dados.

A importação do Excel ainda não grava os dados no estoque. Essa etapa está em desenvolvimento.

## Regras do sistema

- Movimentações estornadas permanecem no histórico, mas deixam de compor o saldo.
- Correções de custo preservam a quantidade e os PDFs da movimentação.
- O recálculo segue a ordem de registro e respeita os ajustes manuais de valor.
- Ajustar o valor atual não modifica o custo das saídas anteriores.
- Produtos com movimentações ou ajustes não podem ser excluídos.
- Correções e estornos exigem justificativa e são registrados na auditoria.
- As alterações relacionadas são salvas em transações, com reversão em caso de erro.

Lançamentos antigos sem informações suficientes de custo podem ter a correção
e o estorno bloqueados, para evitar cálculos incorretos.

## Exemplo de funcionamento

| Movimentação | Quantidade disponível | Valor em estoque |
|---|---:|---:|
| Entrada de 2 unidades a R$ 10,00 | 2 | R$ 20,00 |
| Entrada de 3 unidades a R$ 20,00 | 5 | R$ 80,00 |
| Saída de 2 unidades pelo custo médio de R$ 16,00 | 3 | R$ 48,00 |

Os dados deste exemplo são fictícios.

## Tecnologias

| Tecnologia | Aplicação |
|---|---|
| Python | Regras e integração do sistema |
| Tkinter e ttk | Interface gráfica |
| SQLite e SQL | Armazenamento e consultas |
| Decimal | Cálculos monetários |
| openpyxl | Leitura e geração de Excel |
| pathlib, shutil e uuid | Organização dos anexos |
| JSON | Detalhes dos registros de auditoria |
| unicodedata | Normalização da pesquisa por nome |
| zipfile e tempfile | Backup e restauração |
| Git e GitHub | Controle de versão |

## Aprendizados

- Transformação de necessidades de trabalho em requisitos de sistema.
- Definição de regras de negócio e cenários de teste.
- Funções, condições, laços e tratamento de exceções.
- Consultas SQL com JOIN, SUM, CASE e GROUP BY.
- Transações com commit e rollback.
- Relacionamento entre produtos, movimentações e anexos.
- Validação de quantidades e valores.
- Eventos e atualização de componentes da interface.
- Manipulação de arquivos e criação de backups.
- Custo médio, arredondamento monetário e recálculo de movimentações.
- Preservação do histórico com estornos e auditoria.
- Pesquisa por nome e filtros.
- Commits e organização de repositórios.

## Demonstração

Capturas da versão em desenvolvimento, utilizando dados de teste. Algumas imagens representam versões anteriores à atualização mais recente.

### Tela principal

Cadastro de produtos, consulta das quantidades disponíveis
e acompanhamento do valor total do estoque.

![Tela principal do controle de estoque](tela-inicial.png)

### Registro de saída

Seleção do produto, quantidade, motivo e descrição.
O sistema verifica o saldo antes de confirmar a retirada.

![Janela de registro de saída](registro-saida.png)

### Histórico de movimentações

Consulta das entradas e saídas, com quantidade, motivo,
data e acesso aos PDFs anexados.

A versão atual também apresenta os valores das movimentações e as opções
de correção de custo e estorno.

![Histórico de movimentações](historico-consulta.png)

## Validações realizadas

- Edição dos produtos e persistência após reabrir o programa.
- Exclusão de produtos sem histórico e bloqueio dos que possuem registros.
- Ajuste do valor atual com preservação da quantidade e consulta da auditoria.
- Correção de custo de compra e recálculo das saídas seguintes.
- Estorno com atualização da quantidade e do valor disponível.
- Pesquisa por nome e filtro por categoria.
- Geração e restauração de backup.

Os testes finais gerais e a validação em outro computador ainda fazem parte
das próximas etapas.

## Próximas melhorias

- [ ] Exibição do custo médio na tabela principal.
- [ ] Importação completa do Excel com coluna de custo.
- [ ] Identificação da tabela em diferentes linhas e colunas do Excel.
- [ ] Reconhecimento de cabeçalhos em ordens diferentes.
- [ ] Validação e prévia antes da confirmação da importação.
- [ ] Inicialização automática de uma instalação nova.
- [ ] Organização das pastas de dados para instalação.
- [ ] Revisão dos scripts antigos para manter as regras consistentes.
- [ ] Modernização da interface e adaptação a diferentes telas.
- [ ] Personalização com nome e logo da empresa em JPG, JPEG ou PNG.
- [ ] Inclusão da personalização no backup e na restauração.
- [ ] Testes finais e validação em outro computador.
- [ ] Executável e instalador para Windows.

## Código-fonte e privacidade

Este repositório apresenta o projeto publicamente.
O código-fonte permanece em um repositório privado.

Bancos de dados, documentos pessoais e backups não são publicados nesta vitrine.

A versão atual funciona localmente em um computador e ainda não possui instalador distribuído.

## Autor

**Thiago Dantas**  
Estudante de Análise e Desenvolvimento de Sistemas.

[Meu perfil no GitHub](https://github.com/gromjow10)
