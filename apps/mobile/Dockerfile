FROM cirrusci/flutter:stable

# Cria usuário flutteruser
RUN useradd -ms /bin/bash flutteruser

# Instala dependências Linux necessárias para build
USER root
RUN apt-get update && apt-get install -y \
    cmake \
    ninja-build \
    pkg-config \
    libgtk-3-dev \
    clang \
    git \
 && rm -rf /var/lib/apt/lists/*

# Ajusta permissões do Flutter SDK
RUN chown -R flutteruser:flutteruser /sdks/flutter

# Volta para o usuário normal
USER flutteruser

WORKDIR /home/flutteruser/app

# Copia pubspec primeiro (para cache)
COPY pubspec.* ./
RUN flutter pub get || echo "Nenhum pubspec.yaml encontrado, pulando flutter pub get"

# Copia o restante do código
COPY . .

EXPOSE 8080

CMD ["sh"]
