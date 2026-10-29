# Curare 1.1 — Relatório real de validação

**Tipo:** protótipo acadêmico offline. **Data da revisão:** 29/10/2026.

## Resultado final

| Etapa | Resultado | Evidência |
|---|---|---|
| Revisão da estrutura Android | PASSOU | Arquivos e rotas essenciais presentes |
| XML/AndroidManifest | PASSOU | XML parseado sem erros |
| Restrições de privacidade do protótipo | PASSOU na inspeção estática | Sem `INTERNET`; backup desativado |
| Testes puros Kotlin/JVM | PASSOU | 36 verificações, executadas localmente |
| Kotlin/Compose e código Android | NÃO COMPILADO | SDK, plugin Android e dependências ausentes |
| Testes JUnit via Gradle | NÃO EXECUTADOS | Sem Gradle disponível |
| Geração de APK debug | NÃO EXECUTADA | Build impossível neste ambiente |
| Instalação/uso em Android | NÃO EXECUTADO | Sem dispositivo/emulador acessível |
| Testes visuais e acessibilidade de sistema | NÃO EXECUTADOS | Exigem execução real |

## Melhorias em relação à Fase 3

1. Busca considera pedidos locais já existentes para indicar prestadores com horário efetivamente livre nas próximas duas semanas.
2. Regra de agendamento impede escolher data fora da janela de 14 dias e contratar o próprio perfil local.
3. Cancelamento de pedido exige confirmação; pedidos cancelados deixam de ocupar faixas de horário no demonstrativo.
4. Dias de agendamento usam faixa rolável para se adaptar a telas estreitas.
5. Cadastro retorna ao agendamento ou chat originalmente solicitado.
6. Melhor contraste para textos de apoio e menu da tela inicial.
7. Conversas mantidas em no máximo 500 mensagens locais na memória e persistência.
8. Leitura de pedidos armazenados ignora intervalos inválidos ou campos essenciais ausentes.
9. Três testes JUnit de regressão adicionais e 36 verificações Kotlin/JVM independentes de Android.
10. Workflow CI com permissões mínimas, stack trace e relatório de testes como artifact.

## Como reproduzir os testes executados

```sh
bash checks/verificar-kotlin.sh
python3 checks/verificar-projeto.py
```

## Como gerar o APK real

Abrir no Android Studio com JDK 17, SDK 36 e Gradle 8.13 e executar `:app:testDebugUnitTest` seguido de `:app:assembleDebug`. Ou enviar a pasta do projeto para um repositório GitHub e acionar `.github/workflows/gerar-apk.yml`. Se a compilação terminar com sucesso, o APK estará em `app/build/outputs/apk/debug/app-debug.apk` (Android Studio) ou no artifact `Curare-v1.1-APK-debug` (GitHub Actions).

**Atenção:** nenhuma dessas opções foi executada aqui e nenhum APK foi entregue. Um APK só deve ser considerado validado depois de compilar, instalar e testar os fluxos em dispositivo Android.
