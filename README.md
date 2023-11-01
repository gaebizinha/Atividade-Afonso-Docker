# Atividade Docker Compose

# O que é Docker Compose

Docker Compose é uma ferramenta que permite configurar e executar facilmente aplicativos Docker com vários conteúdos. Ele é usado para gerenciar a configuração de vários contêineres Docker. Com o Docker Compose, você pode definir os serviços, redes e volumes necessários para sua aplicação em um único arquivo chamado “Docker-compose.yml”.

# O que é e como ocorre a transmissão de mensagens pelo Producer/Consumer?

A transmissão de mensagens por meio do modelo Produtor/Consumidor é um padrão de comunicação que permite que diferentes partes do sistema se comuniquem de maneira assíncrona e eficiente. Esse modelo é comumente usado em sistemas de troca de mensagens, filas de mensagens e implementações de sistemas distribuídos. 

Produtor:

- Gera ou produz mensagens, informações ou dados.
- Ele as envia para uma fila para que os consumidores possam acessá-las.

Fila:

- A fila é o local onde as mensagens produzidas pelos produtores são armazenadas temporariamente.
- Os consumidores retiram as mensagens da fila conforme necessário.

1. Consumidor:
    - O consumidor é uma entidade ou componente que retira mensagens da fila e processa essas mensagens.

Um exemplo comum de uso do modelo Produtor/Consumidor é em sistemas de filas de mensagens, como Apache Kafka ou RabbitMQ.

# Manual de instruções:

<aside>
<img src="https://www.notion.so/icons/notification_gray.svg" alt="https://www.notion.so/icons/notification_gray.svg" width="40px" /> Na tarefa o exercício será feito todo pelo Visual Studio Code a partir do seu terminal

</aside>

1. Baixe os arquivos do git e abra-os no Visual Studio Code
2. Abra a aplicação do docker descktop na sua máquina
3. Volte ao Visual Studio Code e abra o terminal, nele você deve digitar o seguinte código:
    
    ```bash
    docker-compose up -d
    ```
    
    Após clicar em enter, espere até serem concluídos os:
    
    - kafka-manager
    - zookeeper
    - kafka
    
    Além disso serão criados os Containers do docker compose.
    
4. Agora escreva no terminal outra mensagem:
    
    ```bash
    docker ps
    ```
    
    Assim será possível visualizar quais dockers forma criados.
    
5. Para criar um tópico é preciso digitar no terminal o seguinte comando:
    
    ```bash
    docker exec -it atividade-afonso-docker-kafka-1 /opt/kafka/bin/kafka-topics.sh --create --topic test-topic --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
    ```
    
    <aside>
    <img src="https://www.notion.so/icons/question-mark_gray.svg" alt="https://www.notion.so/icons/question-mark_gray.svg" width="40px" /> Caso apareça o seguinte erro:
    
    Error while executing topic command : Topic 'test-topic' already exists.
    [2023-11-01 13:43:47,496] ERROR org.apache.kafka.common.errors.TopicExistsException: Topic 'test-topic' already exists.
    
    (kafka.admin.TopicCommand$)
    
    Não se preocupe, ela só está notificando que já existe o tópico e pode desconsidera-lá e siga para o próximo passo.
    
    </aside>
    
6. Por fim, para criar o PRODUCER escreva o seguinte comando:
    
    ```bash
    docker exec -it atividade-afonso-docker-kafka-1 /opt/kafka/bin/kafka-console-producer.sh --topic test-topic --bootstrap-server localhost:9092
    ```
    
7. E para criar o CONSUMER, abra outro terminal sem fechar o anterior e digite:
    
    ```bash
    docker exec -it atividade-afonso-docker-kafka-1 /opt/kafka/bin/kafka-console-consumer.sh --topic test-topic --bootstrap-server localhost:9092
    ```
    

Pronto agora você volta ao primeiro terminal, PRODUCER, e digite o que quiser e clique em enter, assim você pode mudar para o outro terminal cridado, no caso o CONSUMER, e visualizar a mensagem criada.
