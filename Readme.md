# Projeto Ferrari

## Iniciando o projeto

### package.json inicial

O package.json vai crescendo ao longo do projeto, na medida em que vão surgindo necessidades de novas dependências. Inicialmente ele precisa do sass v. 1.

#### Destaques

Além dos nomes de campos autoexplicativos, os destaques são:

* **description** - pode conter uma breve descrição do projeto;
* **scripts** - contém comamandos que podem ser dados por meio do npm/yarn;
* **license** - informa que tipo de licensa será fornecida para o projeto. Essa é uma informação importante para determinar como o sistema poderá ser copiado/usado;
* **devDependencies** - módulos que são instalados para a execução da aplicação.

~~~ json
{
  "name": "ferrari-2.0",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "sass": "sass --watch assets/sass/main.scss:assets/css/main.css"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "sass": "^1.26.10"
  }
}
~~~

#### Instalação das dependências

As dependências são instaladas com o pacote npm conforme abaixo:

`run npm install`

### .gitignore

O .gitignore é um arquivo do git que ignora qualquer pasta e/ou arquivo que esteja listado nele, impedindo a atuação do controle de versão sobre eles. Isso evita que estruturas desnecessárias, principalmente pacotes que podem ser facilmente baixados, sejam levadas para o repositório.

~~~ git
node_modules/

package-lock.json
yarn.lock
.vscode/
~~~

### Trabalhando com o sass

* Foi criada a pasta sass dentro do diretório assets;
* Dentro da pasta sass foi criado o arquivo main.scss que será o responsável por enviar toda a estrutura scss para o css. Se o código css for pequeno, pode ser escrito diretamente no main, mas se for muito grande, a melhor opção é utilizá-lo apenas como centralizador de outros códigos scss
* Na mesma pasta assets foi criada a pasta css e dentro dela, o arquivo main.css. é esse arquivo que receberá todo o conteúdo css do main.scss e será carregado pela página html, que recebe a devida formatação.

#### Executando o sass

Para manter o sass monitorando todas as alterações ocorridas no projeto, ele precisa estar rodando em backgroud. No arquivo package.json foi criado um script que deve ser executado todas as vezes que for trabalhar no projeto. Para executar o script, digite `npm run sass` na linha de comando do terminal, que vai executar a seguinte ação para manter o sass rodando: `sass --watch assets/sass/main.scss:assets/css/main.css`.

##### Estrutura do arquivo

* ***sass --watch*** monitora os arquivos em desenvolvimento;
* ***assets/sass/main.scss*** é o endereço do arquivo principal do sass que envia as instruções css para o arquivo main.css;
* `:assets/css/main.css` recebe todo o código css enviado pelo main.scss. Este é o único arquivo que contém a configuração completa do projeto.

**Nota:** Todas as vezes que for retomado o desenvolvimento, deve ser observado se o sass está rodando.

### index.html

#### Ícone na aba do navegador

Os navegadores mais novos aceitam extensões diferentes de arquivos de imagem, para ser usados como ícones na aba de navegação, todavia os sites mais antigos aceitam apenas arquivos com a extensão .ico. O site [https://www.favicon-generator.org/](https://www.favicon-generator.org/) é uma das opções para a conversão de outras imagens em arquivos .ico. Nesse projeto foi exportada a logomarca da Ferrari, com a estensão .svg e o favicon gerou todos os tamanhos possíveis de ícones e devolveu em formato de código, que altera o tamanho da imagem, de acordo com o dispositivo que carregar a aplicação.

**Nota 1:** é importante observar que a imagem a ser convertida em ícone deve estar com o fundo transparente, caso contrário, virá com o fundo retangular branco, causando efeito indesejado na sua exibição no navegador.

**Nota 2:** o href dos links gerados para a tag `<meta>` apontam para a raiz do arquivo html. Nesse projeto a pasta de imagens, onde estão os ícones gerados, está em `assets/images`, portanto as tags devem ser alteradas, apontando o endereço corretamente.

**Nota 3:** as tags `<link>` não são tags que abrem e fecham, portanto deve ser colocada uma / no final da instrução, antes do fechamento da tag de abertura como neste exemplo: `<link rel="apple-touch-icon" sizes="57x57" href="assets/images/apple-icon-57x57.png" />`

**Nota 4:** como boa prática, o arquivo manifest.json, criado pela favicon deve ser levado para a rauiz do projeto e devidamente apontado na tag `<link>`.

##### Tags alteradas

Essas tags exibem as cores do site na barra do chrome no Android. Elas foram alteradas para mostrar a cor da barra de título do projeto.

* `<meta name="msapplication-TileColor" content="#E1DEDD">`
* `<meta name="theme-color" content="#E1DEDD" />`

##### Tag description

Descrição para melhorar o SEO no Google:

* `<meta name="description" content="Conheça a Ferrari Auto Center" />`.

##### Caminho do arquivo css

* `<link rel="stylesheet" href="assets/css/main.css" type="text/css" />`

### manifest.json

Este arquivo contém um array com uma lista que aponta para diferentes formatos na pasta de imagens.

## HTML5 - Instruções Gerais

### HTML - HyperText Markup Language

### Estrutura Básica

~~~ html
  <!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Alinhamento de blocos</title>
</head>
<body>

</body>
</html>
~~~

* `<!DOCTYPE html>` - informa para a aplicação que é um documento tipo html;
* `<html lang="pt-br">` - define o idioma da aplicação. Se for colocado no topo da página, todo o conteúdo será traduzido pelo browser no idioma indicado. Ele também pode ser usado no meio do corpo do código html, alterando o idioma em um trecho específico;
* `<head></head>` - tudo o que estiver entre essas tags é o cabeçalho do site e não será exibido na página. São informações estruturais da aplicação;
* `<meta charset="UTF-8">` - Define o padrão de acentuação de acordo com o idioma. é o código mais usado e que abrange o maior número de países e idiomas diferentes;
* `<meta name="viewport" content="width=device-width, initial-scale=1.0">` - define o formato da tela de acordo com o dispositivo usado;
* `<link rel="stylesheet" href="style.css">` - informa o local onde está armazenado o arquivo css que vai formatar a página;
* `<title>Título do Site</title>` - Informa o título da página que será exibido na aba do browser.

### Tags e Seus Conteúdos

* `<tag>Com conteúdo</tag>`
* `Tag sem conteúdo</tag>` (self closing)
* `<tag atributo="valor">Texto</tag>`
* `<tag atributo="valor"/>`

* Todos os elementos HTML podem ter atributos;
* Os atributos fornecem informações adicionais sobre um elemento;
* Os atributos sempre são definidos na tag de abertura do elemento;
* Os atributos podem ser em pares nome/valor ou apenas nome;
* É possível lincar vários arquivos de texto diferentes;
* As tags indicam onde começa e termina uma marcação;
* Por se tratar de uma linguagem, ela é formada por um conjunto de regras que devem ser observadas;
* Atributos podem se repetir
* O atributo muda o comportamento do conteúdo

### Tags e Atributos Globais

* Atributos globais funcionam ou se repetem em todas as tags
* **Class** define quais classes CSS serão aplicadas no elemento. O nome de uma classe pode ser repetido em vários elementos, fazendo com que todos eles tenham os mesmos atributos
* **Id** define uma identificação única para o elemento
* **Lang** define o idioma
* Se a tag lang estiver definida no início da página, todo o texto será traduzido para aquele idioma, mas se no meio tiver um texto em outro idioma, aquele trecho pode ser mudado o idioma com essa tag
* **Tabindex** permite definir uma ordem para a tecla tab
* **Accesskey** permite definir uma tecla de atalho

## CSS3 - Instruções Gerais

### Estrutura do código CSS

~~~ css
  header, section, footer {
    background : black ;
  }
~~~

* **header, section, footer** - grupo de seletores. Poderia ser apenas um único seletor, como por exemplo, header;
* {} - **Bloco de declarações**. Todas as declarações que alteram o visual do elemento html estão dentro do par de chaves;
* **background** - propriedade da declaração;
* **":"** - separador;
* **black** - valor da declaração;
* **";"** - fim da declaração

### Seletor universal

~~~ css
* {
  background : black;
}
~~~

O "*" é o seletor universal css. Ele dá um reset no html. Neste projeto ele é aplicado na classe default, redefinindo todos os valores iniciais do projeto. Todos os elementos à priori, recebem as configurações desse seletor, para depois ser alteradas de acordo com o layout do projeto.

### Seletor por tipo

~~~ css
  body {
    background : black;
  }
~~~

Esse seletor aplica o estilo diretamente ao elemento html.

### Seletor por classe

~~~ css
  .fundo-preto {
    background : black;
  }
~~~

Esse seletor é aplicado a todas as classes html que tiverem o mesmo nome. o código css de uma classe é sempre iniciado pelo "." e o nome da classe, conforme o exemplo acima. Uma classe pode ser repetida no html.

### Seletor por ID

~~~ css
  #nome {
    background : black;
  }
~~~

O seletor por ID começa com "#". Uma página só pode ter um único ID.

### Seletor por atributo

~~~ css
  [typ=text] {
    background : black;
  }
~~~

O seletor por atributo ignora outros seletores que possam existir. No exemplo acima, mesmo que o elemento, classe ou ID de uma tag tenha recebido outras configurações, ao aplicar o seletor por atributo, ele prevalecerá aos demais.

### Seletor por pseudo

~~~ css
  :hover {
    background : black;
  }
~~~

Esses são seletores de comportamento. No exemplo acima, ao passar o mouse sobre o elemento, ele fica com a cor preta. Ele pode ser usado em combinação com outro tipo de seletor para atingir um comportamento específico.

## Como funciona a propriedade display

No exemplo do código html acima, a lista ul (unordered list ou lista não ordenada), por padrão vem com display block, indicando que o bloco ul vai ocupar 100% da largura da página.

### O que é um bloco

um bloco é definido por um elemento que permite ter outros elementos dentro dele e que vai ocupar uma área do site.

Um elemento de bloco, sempre vai gerar uma nova linha, mesmo tendo espaço em branco à sua direita ou esquerda.

existem elementos que são, por padrão, elementos de linha, ou seja, display in line.

Com o css é possível mudar o comportamento do bloco, permitindo que ele tenha comportamento de linha ou coluna.

**Nota:** se o css de um elemento de bloco for alterado, mas internamente tiver um elemento que se comporte de maneira diferente, vai interferir no seu comportamento.

### Seletores CSS
