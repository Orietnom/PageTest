# PageTest
Extração de arquivos do portal dados.gov

Esta automação foi realizada em UiPath

A automação se inicia com a declaração de variáveis de ambiente para a criação de pastas necessárias à execução
Em seguida é abrerto o portal https://dados.gov.br/dados/conjuntos-dados/cadastro-nacional-da-pessoa-juridica---cnpj com o navegador Google Chrome

Dicionário de Dados do Cadastro Nacional
	Na aba de recursos, é obtido a data da última atualização do arquivo relacionado a Dicionário de Dados do Cadastro Nacional da Pessoa Jurídica
	Caso haja algum conteúdo no diretório correspondente, o sistema verifica, com base no nome, se o arquivo do portal é mais recente.
	Se o arquivo do portal for mais recente, o download é realizado
	Para o download foi adicionado uma lógica para tentar 3 vezes caso aconteça algum erro
	Para esse arquivo em específico, um .pdf, foi necessário utilizar o atalho de teclado "Ctrl + S" para abrir a janela de salvar como e o arquivo é salvo
	Se o arquivo do portal não for mais recente, é enviado um email alertando que o arquivo no diretório já corresponde ao mais atualizado.

DADOS ABERTOS CNPJ
	Em seguida é acessada a página DADOS ABERTOS CNPJ, e clicado na primeira pasta com data
	É obtida a tabela de arquivos como um data table
	É realizada a mesma verificação de data do arquivo anterior, porém o arquivo baixado é .zip, além da mesma lógica de retentativa
	Caso o arquivo do site seja mais recente é realizado uma ação de enviar a url de download, que abre automaticamente a janela de salvar
	Todos os arquivos da tabela exceto o "Naturezas.zip" são baixados

Ao finalizar a automação um email é enviado avisando que todos os arquivos estão disponíveis no diretório.
