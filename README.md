# Estudo de Caso: Sistema de Gerenciamento de Conteúdo Digital

## Descrição do Problema

Uma empresa deseja criar um sistema para gerenciar empréstimos de livros digitais (e-books) e audiolivros. Este sistema permitirá que os usuários façam o download ou o streaming de conteúdos após a realização de um cadastro e a aquisição de uma assinatura. O sistema também deve controlar a quantidade de licenças disponíveis para cada conteúdo e garantir que os usuários não excedam o número permitido de empréstimos simultâneos.

Os alunos devem colaborar no levantamento de requisitos com base nas necessidades do sistema, criando um banco de dados que permita organizar todas as informações necessárias. O projeto incluirá desde a identificação das entidades e seus relacionamentos até a modelagem lógica e física do banco de dados.

## Objetivos de Aprendizagem

Com este estudo de caso, os alunos deverão ser capazes de:

1. **Analisar Requisitos:** Trabalhar em conjunto para levantar os requisitos necessários para o sistema.
2. **Modelar Banco de Dados:** Criar um modelo *conceitual, *lógico e físico* para armazenar todas as informações necessárias para o sistema.

---

## 1 - Levantamento de **requisitos**

### Perguntas para Levantamento de Requisitos
1. **Quais informações precisam ser armazenadas sobre os usuários?**
   - *Resposta*: Precisamos armazenar o nome, e-mail, senha, data de nascimento, endereço e o status da assinatura (ativa ou inativa).
2. **Como funcionará o sistema de assinatura dos usuários?**
   - *Resposta*: Os usuários precisarão adquirir uma assinatura mensal ou anual para ter acesso ao conteúdo. A assinatura será renovada automaticamente, e o sistema deve controlar a validade da assinatura.
3. **Quantos dispositivos podem acessar o conteúdo ao mesmo tempo com uma única assinatura?**
   - *Resposta*: No momento, cada usuário pode acessar o conteúdo em apenas um único dispositivo ao mesmo tempo.

4. **Há alguma limitação quanto ao número de conteúdos que um usuário pode acessar por vez?**
   - *Resposta*: Não há limite para o número de conteúdos, desde que seja dentro dos dispositivos permitidos e que o usuário possua uma assinatura ativa.
  ****
5. **Quais informações serão armazenadas sobre os livros digitais e audiolivros?**
   - *Resposta*: Precisamos armazenar o título, autor, tipo de conteúdo (e-book ou audiolivro), gênero, número de páginas ou duração.

6. **O sistema precisa controlar downloads e streaming?**
   - *Resposta*: Não, os usuários poderão acessar o conteúdo apenas via streaming na plataforma, sem opção de download.
  
7. **O sistema deve permitir recomendações personalizadas para os usuários?**
   - *Resposta*: Sim, o sistema deve sugerir novos conteúdos com base no histórico de empréstimos e nas preferências do usuário (por exemplo, gênero ou autor favorito).

8. **Como os usuários poderão buscar e filtrar os conteúdos disponíveis?**
   - *Resposta*: O sistema deve permitir que os usuários busquem por título, autor, gênero e avaliações. Também deve incluir filtros para categorias, como “mais populares” ou “novidades”.
  
9. **Como será o processo de notificação para os usuários sobre a validade da assinatura?**
    - *Resposta*: O sistema enviará notificações por e-mail ou através da plataforma, lembrando os usuários sobre a validade da assinatura e avisando sobre renovações ou falhas de pagamento.

10. **O sistema precisa limitar o tempo de inatividade antes de desconectar automaticamente o usuário?**
    - *Resposta*: Sim, por razões de segurança, o sistema deve desconectar automaticamente após 30 minutos de inatividade.

### Requisitos Funcionais

| ID  | Requisito                                                                                 | Descrição                                                                                                              |
| --- | ----------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| RF1 | Armazenamento de informações dos usuários                                                 | Nome, e-mail, senha, data de nascimento, endereço e status da assinatura serão armazenados no sistema.                  |
| RF2 | Sistema de assinatura                                                                     | Usuários adquirem assinatura mensal ou anual, com renovação automática e controle de validade.                         |
| RF3 | Limite de dispositivos simultâneos                                                        | Um usuário pode acessar o conteúdo em apenas um dispositivo por vez.                                                   |
| RF4 | Acesso ilimitado ao conteúdo                                                              | Usuários podem acessar qualquer número de conteúdos, dentro das regras de assinatura e dispositivos.                    |
| RF5 | Armazenamento de informações sobre e-books e audiolivros                                  | Título, autor, tipo de conteúdo, gênero, número de páginas ou duração serão armazenados para cada conteúdo.             |
| RF6 | Acesso ao conteúdo via streaming                                                          | Conteúdos são acessíveis apenas por streaming, sem opção de download.                                                  |
| RF7 | Recomendações personalizadas                                                              | Sugestões de conteúdo baseadas no histórico e nas preferências do usuário.                                             |
| RF8 | Busca e filtros de conteúdo                                                               | Usuários podem buscar e filtrar conteúdo por título, autor, gênero e outras categorias como “mais populares” ou “novidades”. |
| RF9 | Notificação sobre validade de assinatura                                                  | Notificações sobre a validade da assinatura e status de pagamento enviadas por e-mail ou plataforma.                    |
| RF10 | Limite de inatividade para desconexão automática                                         | O sistema desconecta automaticamente usuários após 30 minutos de inatividade.                                           |

### Requisitos Não Funcionais

| ID   | Requisito                                   | Descrição                                                                                                     |
| ---- | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| RNF1 | Segurança de dados                          | Informações de usuários e assinaturas devem ser protegidas com criptografia e armazenamento seguro.           |
| RNF2 | Desempenho                                  | O sistema deve permitir acessos simultâneos sem prejudicar a experiência dos usuários, especialmente no streaming. |
| RNF3 | Escalabilidade                              | A estrutura deve permitir aumento de usuários, conteúdos e dispositivos suportados sem impacto na performance. |
| RNF4 | Conformidade                                | O sistema deve estar em conformidade com a LGPD para proteger os dados dos usuários.                           |
| RNF5 | Disponibilidade                             | O sistema precisa ter uma alta taxa de disponibilidade, com mecanismos de recuperação em caso de falhas.       |
| RNF6 | Suporte a múltiplos dispositivos            | O sistema deve suportar acessos de diferentes tipos de dispositivos (computadores, tablets, smartphones).      |
| RNF7 | Interface amigável                          | A plataforma deve oferecer uma interface fácil de usar e intuitiva para os usuários.                           |
| RNF8 | Manutenção e atualização                    | O sistema deve permitir atualizações frequentes sem interrupção dos serviços para os usuários.                 |
| RNF9 | Auditoria de acessos                        | O sistema deve registrar logs de acessos e ações dos usuários para fins de auditoria e segurança.              |
| RNF10 | Integração com sistema de pagamento         | Deve haver integração com serviços de pagamento para garantir a renovação automática de assinaturas.           |