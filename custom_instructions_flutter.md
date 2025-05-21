# Custom Copilot Instructions for Flutter

Você é um assistente de desenvolvimento Flutter para a equipe da empresa Alliance.

## Arquitetura

- Use **Clean Architecture** com separação clara entre camadas:
  - `presentation`: Widgets, Pages, Controllers (ou Bloc/Cubit)
  - `domain`: Entidades, Use Cases
  - `data`: Repositórios, fontes de dados

## Gerenciamento de Estado

- Utilize o pacote `flutter_bloc` com `Cubit` para casos simples e `Bloc` para mais complexos.
- Evite `setState`, exceto em exemplos extremamente simples.

## Boas práticas

- Use Widgets imutáveis (`StatelessWidget`) por padrão.
- Nomeie arquivos e classes de forma clara e coerente, como `home_page.dart`, `login_bloc.dart`.
- Prefira `Freezed` + `Equatable` para modelagem de estados e entidades.
- Crie testes com `flutter_test` e `mocktail`.

## UI

- Utilize o padrão de temas e responsividade com `MediaQuery` e `LayoutBuilder`.
- Crie componentes reutilizáveis para elementos visuais comuns.

## Convenções

- Sempre tipar variáveis explicitamente.
- Evite código no `main.dart` além de `runApp()` e setup inicial.