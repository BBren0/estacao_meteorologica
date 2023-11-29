# estacao_meteorologica
graph TD
subgraph "Configuração Inicial"
 A[Configurar a comunicação serial]
 B[Definir credenciais Wi-Fi e do servidor Blynk]
 C[Iniciar os sensores e temporizadores]
end
subgraph "Conexão Wi-Fi"
 D[Tentar conectar-se à rede Wi-Fi]
 E[Repetir a tentativa a cada 5 segundos até a conexão]
end
subgraph "Loop Principal"
 F[Executar as tarefas agendadas pelos temporizadores]
 G[Atualizar o serviço Blynk]
end
subgraph "Função de Leitura de Sensores"
 H[Ler a temperatura, umidade, luminosidade, pressão, direção e encoder]
end
subgraph "Função de Cálculo de Médias"
 I[Calcular médias exponenciais para temperatura, umidade, luminosidade e pressão]
end
subgraph "Envio de Dados para o Servidor Remoto"
 J[Enviar dados dos sensores para o servidor remoto via HTTP POST em formato JSON]
end
subgraph "Função de Contagem de Pulsos (Encoder)"
 K[Contar os pulsos do encoder e calcular a rotação em RPM]
end
A --> B
B --> C
C --> D
D --> E
E -->|Conexão estabelecida| F
E -->|Conexão não estabelecida| D
F --> G
G --> F
F --> H
H --> I
I --> J
J --> F
F --> K
K --> F
