Alinhamento com os Objetivos de Desenvolvimento Sustentável (ODS)
O projeto Sistema de Banco de Doações e Trocas Comunitárias está alinhado ao Objetivo de Desenvolvimento Sustentável 11 (ODS 11) – Cidades e Comunidades Sustentáveis.
O sistema Conecta Doações contribui diretamente para esse propósito ao:
•	Incentivar o reaproveitamento de itens, reduzindo o descarte inadequado e, consequentemente, os impactos ambientais;
•	Promover a solidariedade comunitária, ao conectar pessoas dispostas a doar com aquelas que necessitam de apoio;
•	Estimular o consumo consciente e responsável, favorecendo práticas de economia circular;
•	Fortalecer a integração social, criando um ambiente colaborativo que valoriza o compartilhamento e a sustentabilidade.
Regras de Negócio
1.	Um usuário deve estar cadastrado e logado para cadastrar, reservar ou propor trocas de itens.
2.	Cada item pode ser reservado por apenas um usuário por vez.
3.	Itens só podem ser excluídos ou alterados pelo doador que os cadastrou.
4.	Um item reservado não pode ser editado até que a reserva seja concluída ou cancelada.
5.	Apenas itens em boas condições podem ser cadastrados (regra apresentada no termo de uso).
Histórias de Usuário ou casos de uso
•	- Como doador, quero cadastrar um item com foto e descrição para disponibilizá-lo para doação.
•	- Como receptor, quero buscar itens por categoria para encontrar mais facilmente o que preciso.
•	- Como usuário, quero visualizar itens próximos a mim no mapa para facilitar a retirada.
•	- Como receptor, quero reservar um item para garantir que ele seja meu antes de outra pessoa.
•	- Como usuário, quero integrar minha conta ao WhatsApp para conversar rapidamente com o doador.

Perfis de Usuários
Doador: cadastra itens, gerencia seus anúncios e interage com receptores ou outros usuários para troca.
Receptor: busca itens, faz reservas e propõe trocas.
Administrador: gerencia denúncias, garante a integridade e funcionamento da plataforma.
Requisitos funcionais e não funcionais para o sistema Conecta Doações.
Requisitos Funcionais (RF)
1.	RF01 – Login e Cadastro de Usuário
O sistema deve permitir que usuários se cadastrem e façam login utilizando e-mail e senha.
2.	RF02 – Tela Inicial com listagem de itens
O sistema deve exibir uma tela inicial com cards de itens disponíveis para doação ou troca, adequando o layout para web (horizontal) e mobile (vertical).
3.	RF03 – Cadastro de Itens
O sistema deve permitir que doadores cadastrem itens, informando título, descrição, categoria, condição do item e foto.
4.	RF04 – Exclusão de Itens
O sistema deve permitir que o doador visualize e exclua itens cadastrados.
5.	RF05 – Alteração de Itens
O sistema deve permitir que o doador edite informações de itens já cadastrados.
6.	RF06 – Busca de Itens
O sistema deve permitir que os receptores busquem itens por meio de uma barra de pesquisa.
7.	RF07 – Visualização no Mapa
O sistema deve exibir a localização dos itens em um mapa interativo, com filtros de pesquisa e visualização diferenciada para web e mobile.
8.	RF08 – Reservas de Itens
O sistema deve permitir que receptores reservem itens de interesse.
9.	RF09 – Proposta de Troca
O sistema deve permitir que usuários proponham trocas de itens com outros usuários.
10.	RF10 – Confirmação de Ações
O sistema deve exibir mensagens de confirmação (ex: “Item cadastrado com sucesso!”, “Item alterado com sucesso!”, “Item reservado com sucesso!”).
11.	RF11 – Integração com WhatsApp
O sistema deve oferecer opção de integração com WhatsApp para facilitar a comunicação entre doador e receptor.
12.	RF12 – Configurações de Perfil
O sistema deve permitir que o usuário edite informações pessoais e preferências.
Requisitos Não Funcionais (RNF)
1.	RNF01 – Usabilidade
O sistema deve possuir interface simples e intuitiva, adaptada para web e mobile, com navegação consistente.
2.	RNF02 – Responsividade
O sistema deve se adaptar a diferentes tamanhos de tela (desktop, tablet e smartphone).
3.	RNF03 – Performance
O sistema deve carregar as telas principais (Login, Inicial e Busca) em até 3 segundos em conexão estável.
4.	RNF04 – Segurança
O sistema deve criptografar senhas de usuários e proteger dados pessoais conforme a LGPD.
5.	RNF05 – Disponibilidade
O sistema deve estar disponível 24h por dia, 7 dias por semana, com tempo de inatividade mínimo.
6.	RNF06 – Escalabilidade
O sistema deve ser capaz de suportar aumento no número de usuários sem perda significativa de desempenho.
7.	RNF07 – Compatibilidade
O sistema deve ser compatível com os principais navegadores (Chrome, Firefox, Edge) e sistemas operacionais mobile (Android e iOS).
8.	RNF08 – Acessibilidade
10.	RNF10 – Manutenibilidade
O código do sistema deve ser estruturado e documentado, permitindo futuras manutenções e melhorias.

