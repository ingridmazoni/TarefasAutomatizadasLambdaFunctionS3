# TarefasAutomatizadasLambdaFunctionS3


O LocalStack é uma ferramenta que simula serviços AWS localmente para testes e desenvolvimento. Passos básicos para usar com Java:
Instale o LocalStack Via Docker: docker run -d -p 4566:4566 -p 4571:4571 localstack/localstack
Adicione dependências no Maven Inclua no pom.xml:

<dependency>
    <groupId>cloud.localstack</groupId>
    <artifactId>localstack-utils</artifactId>
    <version>0.2.23</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>com.amazonaws</groupId>
    <artifactId>aws-java-sdk-s3</artifactId>
    <version>1.12.700</version>
</dependency>

Configure o endpoint nos testes Exemplo para S3:

AmazonS3 s3Client = AmazonS3ClientBuilder.standard()
    .withEndpointConfiguration(
        new AwsClientBuilder.EndpointConfiguration("http://localhost:4566", "us-east-1"))
    .withCredentials(new AWSStaticCredentialsProvider(
        new BasicAWSCredentials("test", "test")))
    .build();

Execute operações normalmente Crie buckets, envie arquivos, etc. O LocalStack simula o serviço.

Resumo:
Use LocalStack para simular AWS.
Configure o endpoint para localhost:4566.
Ideal para testes automatizados sem custos AWS.



Para configurar a AWS localmente com LocalStack, siga estes passos:
1. Instale o LocalStack via Docker:
docker run -d -p 4566:4566 -p 4571:4571 localstack/localstack

<dependency>
    <groupId>cloud.localstack</groupId>
    <artifactId>localstack-utils</artifactId>
    <version>0.2.23</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>com.amazonaws</groupId>
    <artifactId>aws-java-sdk-s3</artifactId>
    <version>1.12.700</version>
</dependency>

3. Configure o endpoint nos testes ou na aplicação:
4. 
AmazonS3 s3Client = AmazonS3ClientBuilder.standard()
    .withEndpointConfiguration(
        new AwsClientBuilder.EndpointConfiguration("http://localhost:4566", "us-east-1"))
    .withCredentials(new AWSStaticCredentialsProvider(
        new BasicAWSCredentials("test", "test")))
    .build();


AmazonS3 s3Client = AmazonS3ClientBuilder.standard()
    .withEndpointConfiguration(
        new AwsClientBuilder.EndpointConfiguration("http://localhost:4566", "us-east-1"))
    .withCredentials(new AWSStaticCredentialsProvider(
        new BasicAWSCredentials("test", "test")))
    .build();

4. Use normalmente os serviços AWS simulados (S3, Lambda, etc).

