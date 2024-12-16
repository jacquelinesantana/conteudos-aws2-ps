# S3 site estático

1. criar o bucket
   
   1. na console da AWS pesquisar pelo serviço S3
   
   2. clicar no botão "Criar bucket"
   
   3. tipo de bucket: propósito geral
   
   4. dar um nome unico ao seu bucket, não pode ter outro igual globalmente
   
   5. propriedade do objeto deixar desabilitada a opção do ACLs
   
   6. configuração de bloqueio do acesso público deste bucket vamos desmarcar a opção "bloquear todo o acesso público"
   
   7. marcar a opção "reconheço que as configurações atuais podem fazer com que este bucket e os objetos dentro dele se tornem públicos"
   
   8. ir direto para botão "Criar bucket"

2. clique sobre o seu bucket

3. guia "propriedades"

4. em hospedagem de site estático vamos clicar em "editar"
   
   1. em Hospedagem de site estático vamos selecionar a opção 'ativar'
   
   2. tipo de hospedagem vamos selecionar "hospedagem de site estático"
   
   3. codumento de indice, vamos preencher com index.html
   
   4. documento de erro vamos preencher com error.html
   
   5. clicar em Salvar alterações

5. na guia "permissões" vamos até a parte do "política do bucket"
   
   1. clique no botão editar



```
{
     "Version": "2012-10-17", 
     "Statement": 
        [ 
            { 
                "Effect": "Allow", 
                "Principal": "*", 
                "Action": "s3:GetObject", 
                "Resource": "arn:aws:s3:::meusite-exemplo/*" 
            } 
        ]
}
```



2. ajustar o nome do bucket para o nome que vc deu ao bucket

3. clicar em "salvar alterações"

6. abrir a guia "Objetos"
   
   1. incluir os arquivos HTML
   
   2. clicar em "Carregar"
   
   3. abrir o endereço público do bucket
