
# Flutter App Base - Clean Architecture

Este repositório serve como base para projetos Flutter utilizando a arquitetura limpa (Clean Architecture), seguindo os padrões definidos pela equipe da Alliance.

## Estrutura de Pastas

- `lib/presentation` — Widgets, páginas, controllers (Bloc/Cubit)
- `lib/domain` — Entidades e casos de uso
- `lib/data` — Repositórios e fontes de dados

## Padrões Utilizados

- Gerenciamento de estado com `flutter_bloc`
- Modelagem com `Freezed` e `Equatable`
- Testes com `flutter_test` e `mocktail`
- Responsividade com `MediaQuery` e `LayoutBuilder`

## Requisitos

- Flutter SDK
- Dart >= 3.x
- Pacotes: `flutter_bloc`, `freezed`, `equatable`, `get_it`, entre outros

## Como iniciar

```bash
flutter pub get
flutter run
```

## Convenções

- Utilizar `StatelessWidget` por padrão
- Evitar lógica no `main.dart`
- Tipar variáveis explicitamente


## Docker (opcional)

Este projeto Flutter não costuma ser executado via Docker em produção, mas pode-se usar para builds automatizados.

```Dockerfile
# Dockerfile para build Flutter
FROM cirrusci/flutter:stable

WORKDIR /app
COPY . .

RUN flutter pub get
RUN flutter build apk --release
```

## GitHub Actions - CI

```yaml
# .github/workflows/flutter-ci.yml
name: Flutter CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
    - uses: subosito/flutter-action@v2
      with:
        flutter-version: 'stable'
    - run: flutter pub get
    - run: flutter analyze
    - run: flutter test
```