# <b>Códigos de Retorno</b>

As requisições à API podem retornar os seguintes códigos HTTP:

Code / Responses
## <b>200 OK</b>
-  Tudo funcionou como esperado e a validação dos dados foi realizada com sucesso.

## <b>400 Requisição inválida</b>
-  O número de CNPJ informado não é válido.

## <b>401 Não autorizado</b>
-  Problemas durante a autenticação.

## <b>403 Proibido</b>
-  Este erro ocorre quando há algum caminho errado na requisição. Certifique-se de chamar a API da seguinte forma: "https://apigateway.serpro.gov.br/consulta-cnpj-df/v1/cnpj/{ni}"

## <b>404 Não Encontrado</b>
-  Não existe CNPJ com o número de inscrição informado.

## <b>422 Entidade não processada</b>
-  Consulta não realizada - não foi possível recuperar o histórico de eventos.

## <b>500 Erro no servidor</b>
-  Ocorreu algum erro interno no Servidor.

## <b>502 Erro de Integração</b>
-  Ocorreu algum erro de integração que impossibilitou que esta requisição de consulta da API obtivesse os dados solicitados. Não foi possível recuperar o histórico de eventos.

## <b>504 Tempo Esgotado do Gateway</b>
-  Ocorreu algum erro de rede e o gateway não respondeu a tempo. A requisição não chegou até a API Consulta DUE.