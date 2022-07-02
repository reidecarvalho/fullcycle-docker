# A ideia que eu tive para cumprir o desafio foi usar o recurso de multistage build.
# Primeiro eu uso a imagem Go para compilar e depois uso uma imagem mínima (scratch) somente com o executável compilado.

# STAGE 1 #
# Imagem com o framework do Go para compilar. "buider" é um apelido para referenciar esse stage posteriormente
FROM golang AS builder

# Configuro diretório inicial conforme orientado das instruções da imagem no Docker Hub
WORKDIR /usr/src/app

# Cópia do script Go para o Workdir da Imagem
COPY hello-world.go .

# Gera o executável Go
RUN go build hello-world.go


# STAGE 2 - Final #
# Imagem mínima no Docker
FROM scratch

# Diretório inicial, arbitrário.
WORKDIR /app

# Cópia do executável do Go no stage anterior para o diretório atual na nova imagem
COPY --from=builder /usr/src/app/hello-world .

# Roda o executável
ENTRYPOINT ["./hello-world"]