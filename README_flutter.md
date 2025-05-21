
# Flutter App Base - Clean Architecture

Este repositório fornece uma base sólida para aplicações Flutter estruturadas com Clean Architecture, separando responsabilidades em camadas bem definidas, promovendo testabilidade, escalabilidade e manutenibilidade.

## Camadas de Arquitetura

```lib/
├── data/             # Implementações concretas, DTOs e fontes de dados (API, local)
├── domain/           # Entidades puras, interfaces (abstrações) e casos de uso
├── presentation/     # UI, widgets, páginas, controllers (BLoC/Cubit)
├── core/             # Dependências globais, utilitários, constantes, temas, injeção```

> Cada camada conhece apenas a anterior (ex: presentation denpende de domain, mas nunca de data)

## Tecnologias e Padrões Adotados

- Gerenciamento de estado: 	flutter_bloc, [Cubit]
- Modelagem de dados:	Freezed, Equatable
- Testes:	flutter_test, mocktail
- DI (Injeção de dependência):	get_it
- Responsividade:	LayoutBuilder, MediaQuery, Flexible, Expanded
- Estilo Funcional:	Imutabilidade com Freezed e composição de widgets
- Análise Estática:	flutter analyze, suporte a lints personalizadas

## Pré Requisitos

- Flutter SDK >= 3.0.0
- Dart >= 3.0.0

> Ferramentas como Android Studio, VS Code ou outro IDE com suporte a Flutter

## Dependências Essenciais
- dependencies:
-- flutter_bloc: ^8.x
-- freezed_annotation: ^2.x
-- get_it: ^7.x
-- equatable: ^2.x

- dev_dependencies:
-- build_runner: ^2.x
-- freezed: ^2.x
-- mocktail: ^1.x

- flutter_test:
-- sdk: flutter

## Como Rodar o Projeto

```flutter pub get          # Instala dependências```
```flutter run              # Executa o app (dispositivo/emulador padrão)```

## Gerar arquivos com Freezed/JsonSerializable

```flutter pub run build_runner build --delete-conflicting-outputs```

## Boas Práticas

- Utilize StatelessWidget sempre que possível
- Evite lógica de negócio no main.dart — use init() e get_it
- Tipagem explícita para variáveis e funções
- Separe claramente dados, domínio e UI
- Faça testes unitários para casos de uso e cubits/blocs
- Use Theme.of(context) para estilo global e evite hardcoded styles


## Docker (opcional)

Embora o uso de Docker em desenvolvimento Flutter seja raro, ele pode ser útil para pipelines de CI/CD:

```Dockerfile para build automatizado (APK)

FROM cirrusci/flutter:stable

WORKDIR /app
COPY . .

RUN flutter pub get
RUN flutter build apk --release

docker build -t flutter_app_build .
docker run flutter_app_build
```

## GitHub Actions - CI

```
# github/workflows/flutter-ci.yml

name: Flutter CI

on:
  [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Setup Flutter
        uses: subosito/flutter-action@v2
        with:
          flutter-version: 'stable'

      - name: Install Dependencies
        run: flutter pub get

      - name: Analyze Code
        run: flutter analyze

      - name: Run Tests
        run: flutter test
```

## Possíveis Extensões Futuras

- Integração com Firebase/Auth/Firestore
- Suporte a múltiplos temas (dark/light mode com theme_mode)
- Internacionalização com flutter_localizations
- Repositório local com hive, shared_preferences ou isar
- Automação com melos (monorepo)
- Documentação com Dartdoc
