# Use a imagem oficial do Golang como base
FROM golang:1.21 AS builder

# Define o diretório de trabalho dentro do contêiner
WORKDIR /app

# Copie o código fonte para o diretório de trabalho no contêiner
COPY . .

# Construa o aplicativo Go
RUN go build -o api-go-gin .

# Etapa de produção
FROM alpine:latest

# Define o diretório de trabalho dentro do contêiner
WORKDIR /root/

# Copie o binário construído da etapa de construção anterior
COPY --from=builder /app/meuapp .

# Expõe a porta em que o aplicativo vai escutar
EXPOSE 8080

# Comando para iniciar o aplicativo quando o contêiner for iniciado
CMD ["./meuapp"]
