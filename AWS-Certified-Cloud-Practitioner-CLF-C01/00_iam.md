## IAM

Identity Access Management é aquele recurso dentro da AWS, que é server less, que garante que você tem privilégio ou não para iniciar executar qualquer ação dentro da WS.
É nesse ponto que você cria os seus usuários, seus grupos, suas regras e assim por diante.

IBP = Identity Beast Policy -> Utilizado para bloquear uma identidade. 
RBP = Resource Based Policy -> Utilizado para bloquear recurso.

Toda vez que crio algum recurso dentro da AWS, é uma API que verifica meu IAM para validar se eu tenho a permissão e ai sim cria o recurso que eu estou solicitando.

![](images/iam.png)

Quando é criado um usuário ele tem acesso ao:
- Console;
- CLI;
- API;
Mas não tem nenhum privilegio deve ser criado.

``Grupos`` são feitos para agrupar usuários, por exemplo você pode agrupar todos os usuários que são data science pois eles vão utilizar os mesmo recursos da AWS.

``Roles`` são feitas para permitir um serviço acessar o outro por exemplo:
- Eu posso subir uma instancia EC2 e dar a permissão para ele acessar um s3 espeficico.

``Policy`` são regras onde pode se permitir ou bloquear acesso dos grupos ou usuários, por exemplo:
- Posse criar uma policy que permite somente fazer upload ao s3 e direcionar essa policy para algum grupo ou usuário.

<div style="background-color: white; display: inline-block; padding: 10px;">
  <img src="images/u-g-r-p-iam.png" />
</div>

``!NUNCA`` devemos fazer nada na conta **ROOT** o ideal é criarmos uma outra conta com acessos especificos.

Fluxo para cadastro de novo usuário a partir da sua conta root.
![](images/cadastro-novo-usuario.png)

Se o usuário for selecionar os recursos via conselo é interessante orientalo a habilitar o MFA para aumentar ainda mais a segurança.
Agora se o usuário for acessar via ``CLI``, ``API`` o root deve criar uma access key id e uma secret access key para poder manipular os recursos AWS.


<details>
  <summary>🚀 Resumo IAM</summary>

O AWS Identity and Access Management (IAM) é um serviço da AWS que ajuda a controlar quem está autenticado (assinado) e autorizado (tem permissões) para usar os recursos da AWS.

Aqui estão os principais pontos sobre o IAM:

1. Controle Granular de Acesso a AWS: Com o IAM, você pode criar usuários, grupos, papéis e políticas de permissão para controlar o acesso aos serviços e recursos da AWS de uma maneira granular. Por exemplo, você pode permitir que um usuário tenha acesso somente leitura ao Amazon S3 e acesso total ao EC2.

2. Compartilhamento Seguro de Acesso: O IAM permite compartilhar o acesso à sua conta AWS de maneira segura. Em vez de compartilhar suas credenciais de root, você pode criar vários usuários IAM, cada um com suas próprias credenciais e permissões.

3. Identidade Federada: Com o IAM, você também pode permitir usuários que já tenham senhas em outros lugares, como na sua rede corporativa ou em um provedor de identidade baseado em SAML, a obter acesso temporário à sua conta AWS.

4. Compatível com Multi-Fator Authentication (MFA): O IAM é compatível com a autenticação de vários fatores para fornecer uma camada adicional de proteção de segurança ao gerenciar o acesso aos serviços e recursos da AWS.

5. Integrado com AWS Services: O IAM está integrado com todos os serviços da AWS, o que significa que você pode definir permissões para qualquer serviço que desejar.

6. Auditoria com AWS CloudTrail: Com o AWS CloudTrail, você pode registrar todas as ações de usuários e APIs IAM para fins de auditoria.

7. Gratuito: O IAM é um recurso gratuito da AWS; você só paga pelos outros recursos da AWS que seus usuários acessam.

Em suma, o AWS IAM é um serviço de segurança crítico que ajuda a proteger o acesso aos recursos da AWS, permitindo que você controle quem pode fazer o quê em sua conta AWS.
 
</details>

<details>
  <summary>🚀 Resumo MFA</summary>
A Autenticação Multifator (MFA) é um método de controle de acesso que exige que um usuário verifique sua identidade usando duas ou mais evidências (fatores) antes que o acesso seja concedido. Estes fatores podem ser algo que o usuário sabe (como uma senha), algo que o usuário tem (como um telefone celular ou um token de hardware) e algo que o usuário é (como uma impressão digital ou reconhecimento facial).

Aqui estão alguns pontos-chave sobre MFA:

1. Segurança Aprimorada: O principal benefício da MFA é que ela aumenta significativamente a segurança, tornando muito mais difícil para os invasores ganharem acesso não autorizado a um sistema. Mesmo que um fator de autenticação seja comprometido (por exemplo, se uma senha for roubada), os outros fatores ainda protegem o sistema.

2. Diversos Métodos de Autenticação: A MFA pode usar uma variedade de métodos de autenticação, como códigos de verificação por SMS, aplicativos de autenticação, tokens de hardware, impressões digitais, reconhecimento facial e muito mais.

3. Compatibilidade: A MFA é compatível com muitos sistemas e serviços, incluindo a maioria das plataformas de nuvem (como AWS, Google Cloud e Azure), serviços de email, redes sociais, plataformas de pagamento online, entre outros.

4. AWS MFA: A AWS suporta MFA e recomenda que os usuários a utilizem para proteger suas contas. Com a MFA ativada, quando um usuário se conecta à AWS, ele é solicitado a inserir seu nome de usuário e senha (primeiro fator) e um código de autenticação de um dispositivo MFA (segundo fator).

Resumindo, a Autenticação Multifator é uma medida de segurança essencial que protege os sistemas de acesso não autorizado, exigindo que os usuários verifiquem sua identidade com vários fatores de autenticação.
</details>

<details>
  <summary>🚀 Resumo Organizações</summary>
O AWS Organizations é um serviço da AWS que permite a você centralizar e gerenciar de forma unificada várias contas AWS. Com o AWS Organizations, você pode criar uma organização para administrar suas contas da AWS a partir de um único local.

Aqui estão algumas características principais do AWS Organizations:

1. Gerenciamento Centralizado de Contas: O AWS Organizations permite agrupar e gerenciar todas as suas contas AWS de um único local centralizado. Isso facilita o gerenciamento de contas e recursos em uma organização.

2. Controle de Acesso Hierárquico: Com o AWS Organizations, você pode criar uma estrutura hierárquica de Unidades Organizacionais (OUs) para agrupar suas contas. Isso ajuda a organizar suas contas em uma estrutura que melhor se alinhe com o uso dos recursos em sua organização.

3. Políticas de Controle de Serviço: O AWS Organizations oferece políticas de controle de serviço (SCPs) que permitem que você controle as permissões para as contas em sua organização. Isso permite que você aplique regras de acesso uniformes em todas as suas contas.

4. Consolidação de Cobrança: O AWS Organizations também oferece a capacidade de consolidar sua cobrança em todas as suas contas AWS, o que pode simplificar a gestão de custos e permitir um melhor rastreamento e controle dos gastos da AWS.

5. Automação: Com o AWS Organizations, você pode automatizar a criação e o gerenciamento de contas por meio de APIs e integrações com outras ferramentas da AWS, como o AWS CloudFormation.

Em suma, o AWS Organizations é uma ferramenta poderosa para empresas e equipes que gerenciam várias contas da AWS, permitindo o gerenciamento centralizado de contas, a aplicação de políticas em todas as contas, a consolidação de cobranças e a automação de tarefas de gerenciamento de contas.
</details>

