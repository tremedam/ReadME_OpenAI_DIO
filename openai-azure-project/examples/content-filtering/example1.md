# Exemplo de Filtro de Conteúdo com Ferramentas OpenAI

## Descrição
Este exemplo demonstra como aplicar filtros de conteúdo utilizando ferramentas OpenAI. O objetivo é mostrar como configurar e utilizar esses filtros para garantir que o conteúdo gerado atenda a critérios específicos de qualidade e segurança.

## Passo a Passo

1. **Configuração do Ambiente**
   - Certifique-se de que você possui acesso à API da OpenAI e que as credenciais estão configuradas corretamente em seu ambiente de desenvolvimento.

2. **Definição dos Filtros de Conteúdo**
   - Antes de gerar o conteúdo, defina quais tipos de conteúdo você deseja filtrar. Por exemplo, você pode querer evitar linguagem ofensiva, informações sensíveis ou conteúdo irrelevante.

3. **Implementação do Filtro**
   - Utilize a seguinte função para aplicar os filtros desejados ao conteúdo gerado:

   ```python
   import openai

   def gerar_conteudo(prompt):
       resposta = openai.ChatCompletion.create(
           model="gpt-3.5-turbo",
           messages=[{"role": "user", "content": prompt}]
       )
       return resposta['choices'][0]['message']['content']

   def filtrar_conteudo(conteudo):
       # Exemplo de filtro simples
       palavras_proibidas = ["ofensivo", "sensível"]
       for palavra in palavras_proibidas:
           if palavra in conteudo:
               return "Conteúdo filtrado devido a palavras proibidas."
       return conteudo

   prompt = "Escreva um parágrafo sobre tecnologia."
   conteudo_gerado = gerar_conteudo(prompt)
   conteudo_filtrado = filtrar_conteudo(conteudo_gerado)

   print(conteudo_filtrado)
   ```

4. **Resultados Esperados**
   - O conteúdo gerado deve ser exibido no console. Se o conteúdo contiver palavras proibidas, a função de filtro retornará uma mensagem indicando que o conteúdo foi filtrado.

## Conclusão
Este exemplo ilustra como implementar filtros de conteúdo ao utilizar ferramentas OpenAI. É importante adaptar os filtros às necessidades específicas do seu projeto para garantir a qualidade e a segurança do conteúdo gerado.