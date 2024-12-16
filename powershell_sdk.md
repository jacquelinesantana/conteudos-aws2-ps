# AWS PowerShell tools

O _AWS Tools for PowerShell_ permite que desenvolvedores e administradores gerenciem seus serviços da AWS a partir do ambiente de scripts do PowerShell.

_AWS.Tools_ é a nova variante modular do AWS Tools para PowerShell. Para gerenciar cada serviço da AWS, instale a partir da [PowerShell Gallery](https://www.powershellgallery.com/) o módulo correspondente.

A ideia por trás da AWS PowerShell é ter um serviço modular, onde vc baixa e instala os modulos que vai precisar.

É uma ferramenta multiplataforma (Linux, Windows, MacOs)



## Instalação:

1. executar o PowerShell como adm 

2. executar o comando `Install-Module -Name AWS.Tools.Installer`

3. confirmar a instalação digitando S

4. digite s para confirmar a instalação dos pacotes

Resultado esperado:

![2da61650-393d-43f1-ae81-615dc1f2ed5b](file:///C:/Users/Jacqueline/Pictures/Typedown/2da61650-393d-43f1-ae81-615dc1f2ed5b.png)

Site do projeto: [GitHub - aws/aws-tools-for-powershell: The AWS Tools for PowerShell lets developers and administrators manage their AWS services from the PowerShell scripting environment.](https://github.com/aws/aws-tools-for-powershell)

5. para instalar o módulo que permite trabalhar com EC2 e S3 vamos executar o comando:
    Install-AWSToolsModule AWS.Tools.EC2,AWS.Tools.S3 -CleanUp

6. digite A para executar a instalação. Esse processo pode se repetir algumas vezes perguntando se tem certeza que deseja seguir instalando os pacotes.

Resultado esperado:

![f597d159-f670-423e-81cf-d7c02fb8bea5](file:///C:/Users/Jacqueline/Pictures/Typedown/f597d159-f670-423e-81cf-d7c02fb8bea5.png)

7. para permitir a execução de scripts execute o comando: `Set-ExecutionPolicy RemoteSigned `

8. confirme a alteração

9. com o seguinte comando é possível ver os módulos do PowerShell 
   
       Get-Module -ListAvailable

![4fac0777-5406-44f0-8669-389877db0a7d](file:///C:/Users/Jacqueline/Pictures/Typedown/4fac0777-5406-44f0-8669-389877db0a7d.png)

10. ver versão do PowerShell 
    
        Get-AWSPowerShellVersion

Resultado esperado

![fe809ed7-c9ca-48e4-b071-2a2e127ed40f](file:///C:/Users/Jacqueline/Pictures/Typedown/fe809ed7-c9ca-48e4-b071-2a2e127ed40f.png)

11. ver serviços AWS que são suportados, comando: 
    
        Get-AWSPowerShellVersion -ListServiceVersionInfo

Resultado esperado:

![8d741abc-4296-480a-a064-101ce31697ea](file:///C:/Users/Jacqueline/Pictures/Typedown/8d741abc-4296-480a-a064-101ce31697ea.png)

12. ver versão do PowerShell
    
        $PSVersionTable

![0d0b412a-9328-4c59-8fdf-dfd0bee516a5](file:///C:/Users/Jacqueline/Pictures/Typedown/0d0b412a-9328-4c59-8fdf-dfd0bee516a5.png)

13. conectar o seu usuário do IAM ao PowerShell

[Configure tool authentication with AWS - AWS Tools for PowerShell](https://docs.aws.amazon.com/powershell/latest/userguide/creds-idc.html#idc-config-sso)

```
$params = @{ 
    ProfileName = 'my-sso-profile' AccountId = '111122223333' RoleName =     'SamplePermissionSet' SessionName = 'my-sso-session' StartUrl = 'https://provided-    domain.awsapps.com/start' SSORegion = 'us-west-2' RegistrationScopes =     'sso:account:access'
};
Initialize-AWSSSOConfiguration @params
```

14. Substitua os valores da propriedade de exemplo com valores do seu IAM Identity Center Configuração. Para obter informações sobre essas propriedades e como encontrá-las, consulte [as configurações do provedor de credenciais do IAM Identity Center](https://docs.aws.amazon.com/sdkref/latest/guide/feature-sso-credentials.html#feature-sso-credentials-profile) no _Guia de referência de SDKs e ferramentas_ da _AWS_.

## CONFIGURAR CREDENCIAIS

Após a instalação falta colocarmos nossas credenciais para conseguir interagir em nossa conta AWS pelo PowerShell

1. no IAM -> credenciais de segurança

2. Clicar em Criar Chave de Acesso

3. Executar o comando a seguir com os dados das suas chaves de acesso:
   `Set-AWSCredential -AccessKey <AccessKeyID> -SecretKey <SecretAccessKey> -StoreAs Default`
   substituir onde esta <AccessKeyID> e <SecretAccessKey> pelas suas credenciais.

4. Execute o comando a seguir para definir uma região como default pra suas atividades
   `Set-DefaultAWSRegion -Region us-east-1` 

5. Você pode atualizar o Help com o comando: `Update-Help`

#### Modulos que pode ser interessante instalar:

Para usar comandos do IAM`Install-Module -Name AWSPowerShell -Force` 

## Sobre o AWS Tools for PowerShell

### 🔧 AWS Tools for PowerShell

* Específico para ambientes Windows
* Integração nativa com PowerShell
* Cmdlets no estilo PowerShell
* Mais "natural" para administradores Windows
* Melhor integração com ecosistema Microsoft

#### Exemplo de comando:

    Get-S3Bucket
    Get-EC2Instance

#### AWS Tools for PowerShell:

* Infraestrutura 100% Windows
* Active Directory
* Automações específicas Windows
* PowerShell DSC
* Integração com .NET
* Scripts para administração Windows

#### Comparando com o CLI:

🖥️ AWS CLI (Command Line Interface)

- Interface de linha de comando universal
- Funciona em Linux, macOS, Windows
- Escrito em Python
- Comandos padrão para todos os sistemas
- Sintaxe genérica
- Multiplataforma

AWS CLI:

- Ambientes Linux/macOS
- Scripts multiplataforma
- Integração com outras linguagens
- Automações gerais
- Containers
- CI/CD

# SDK AWS

## SDK Java

[Documentação Java - AWS SDK - Amazon Web Services](https://aws.amazon.com/pt/sdk-for-java/)

[GitHub - aws/aws-sdk-java-v2: The official AWS SDK for Java - Version 2](https://github.com/aws/aws-sdk-java-v2/#using-the-sdk) - Pom para projetos Maven

## SDK Python

[AWS SDK para Python](https://aws.amazon.com/pt/sdk-for-python/)

`pip install boto3`





## Comandos powerShell

`Get-S3Bucket` - ver buckets

`New -S3Bucket -BucketName examploNome -Region us-west-1` Criar um novo bucket

`Remove-S3Bucket -BucketName exemploNome -Force` remover o bucket

`Get-S3Object -BucketName "nome-do-bucket" | Remove-S3Object` excluir objetos de um bucket

`Get-EC2Instance` ver as instâncias existentes na conta

`Get-Module AWS* -ListAvailable` ver os módulos disponíveis

`Get-AWSRegion` ver as regiões AWS




