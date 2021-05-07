# PREVISAOtempo
<div id="app"></div>

sqlEstado = 'SELECT * FROM estado ORDER BY nome ASC';
$resEstado = $conexao->prepare($sqlEstado);
$resEstado->execute();
$estados = $resEstado->fetchAll();
Formulário

<form action="salvar_anuncio.php" method="post" enctype="multipart/form-data">

    <label for="estado">Estado:</label>
    <select name="estado" id="estado" required>
        <option value="">Selecione</option>
        <?php foreach ($estados as $estado) { ?>
            <option value="<?php echo $estado['id'] ?>"><?php echo $estado['nome'] ?></option>
        <?php } ?>
    </select>

    <label for="cidade">Cidade:</label>
    <select name="cidade" id="cidade" disabled required>
        <option value="">Selecione um estado</option>
    </select>

    <label for="bairro">Bairro:</label>
    <select name="bairro" id="bairro" disabled required>
        <option value="">Selecione uma cidade</option>
    </select>

    <label for="foto">Foto:</label>
    <input type="file" name="foto" id="foto">

    <button type="submit">Salvar</button>
</form>
Esta tag tem vários parâmetros, vamos ver uma sintaxe completa desta TAG.

<form action="mailto:seumail@provedor?subject=assunto" method="post" enctype="text/plain" name="nome_do_formulario">

</form> Vamos entender esta TAG :

FORM
Indica que estamos iniciando um Formulário
ACTION
Indica a ação que formulário terá, neste caso, o formulário terá os dados enviados para seu e-mail. Pode ser indicado também um servidor e o programa CGI que irá processar o formulário.
SUBJECT
É o assunto do e-mail.
METHOD
É o metodo da troca de dados; qual método o servidor usará para recerber o formulário. Os métodos podem ser POST ou GET, neste caso é POST, porque estamos enviando informação para o provedor. Já o método GET, faz com que o conteúdo do formulário seja anexado ao endereço da URL.
ENCTYPE
É como o formulário será enviado, aqui os dados serão formatados como texto puro.
CAMPOS DO FORMULÁRIO

TIPO TEXTO

<INPUT>

Define um campo de entrada em que o usuário entra com as informações do formulário. Cada campo de um formulário atribui o seu conteúdo para uma variável, que possui nome e tipo específicos. Veja como seria :


<FORM>
DIGITE SEU NOME <input type="text" name="var_nome" size="35" maxlength="30" value="qq coisa">
</FORM>
TYPE="TEXT"
type = tipo - text = texto, ou seja o tipo de informação que aquele local receberá é do tipo texto.
NAME="VAR_NOME"
name = nome - var_nome é a variável que irá guardar o que for digitado naquele campo.
SIZE="35"
tamanho do objeto será de 35 pixels
MAXLENGTH="30"
comprimento máximo de caracteres será de 30.
VALUE = "QUALQUER COISA"
value = valor, ou seja, o campo já vem preenchido com o que vier neste parâmetro, neste caso virá escrito : qq coisa. Para alterar, basta selecionar o texto e escrever outro. Só utilize o value caso queira que um campo já venha preenchido com um valor, por exemplo : estado = SP, ai sim vale a pena.
Veja como ficaria :

DIGITE SEU NOME 
qualquer coisa
TIPO SENHA

E se você quiser que a pessoa entre com uma senha ? Pode usar o type="password" Este comando é idêntico ao comando INPUT TEXT. Sua única diferença é que, no lugar dos caracteres digitados, aparece um asterisco.
Vamos ver como seria :


<FORM>
DIGITE A SENHA <input type="password" name="var_senha" size="10" maxlength="6">
</FORM>
TYPE="PASSWORD"
type = tipo - password = senha, ou seja o tipo de informação que aquele local receberá é do tipo senha, exibirá asterisco ao invés do caracter digitado.
NAME="VAR_SENHA"
name = nome - var_senha é a variável que irá guardar o que for digitado naquele campo.
SIZE="35"
tamanho do objeto será de 10 pixels.
MAXLENGTH="6"
comprimento máximo de caracteres será de 6.
Veja como ficaria :

DIGITE A SENHA 
BOTÃO DE RADIO

E para fazer uma seleção exclusiva de uma lista de opções ? Precisamos inserir um "botão de rádio", que são associados a uma única variável. O conteúdo de um dos campos é atribuído à variável. Apenas um campo pode ser marcado, vamos ver um exemplo :


<FORM>
Digite seu nome:  <input type = "text" name = "var_nome"> 
Estado civil:
<input type=  "radio"  name="civil" value = "solteiro" checked>
Solteiro
<input type=  "radio"  name="civil" value = "casado">
Casado
<input type=  "radio"  name="civil" value = "divorciado">
Divorciado
<input type=  "radio"  name="civil" value = "viúvo">
Viúvo<br>
</FORM>

Observe que todas as variáveis receberam o mesmo nome: CIVIL. Veja também que o único comando que tem o parâmetro CHECKED é o que contém a opção de solteiro,ou seja, esta opção já vem marcada como padrão.
Estas linhas reproduzirão :

Digite seu nome: 

Estado civil:  Solteiro  Casado  Divorciado  Viúvo
OS NOMES DAS OPÇÕES OBRIGATÓRIAMENTE DEVEM SER IGUAIS, SE FOREM DIFERENTES, ESTE POSSIBILITARÁ MARCAR VÁRIAS OPÇÕES !!!

CHECKBOX

Para poder selecionar várias opções, usamos o CHECKBOX. Ele se parece como Radio Button, mas tem uma diferença significativa. Nele mais de um campo associado a uma variável pode ser selecionado. Veja o exemplo:

<FORM>
Digite seu nome:  <input type = "text" name="var_nome"> 
Estado civil:
<input type="radio"  name="civil" value = "solteiro" cheked>
Solteiro
<input type="radio"  name="civil" value = "casado">
Casado<
<input type="radio"  name="civil" value = "divorciado">
Divorciado
<input type="radio"  name="civil" value = "viúvo">
Viúvo
Documentos :
<INPUT TYPE="checkbox" name="teste" value="1"> Carteira de Trabalho
<INPUT TYPE="checkbox" name="teste" value="2"> CIC
<INPUT TYPE="checkbox" name="teste" value= 3"> Carteira de Identidade
</FORM>
Veja o que isso reproduz :

Digite seu nome: 
Estado civil:
 Solteiro  Casado  Divorciado  Viúvo

Documentos :
 Carteira de Trabalho
 CIC
 Carteira de Identidade
LISTA DE OPÇÕES

o comando <SELECT> ... </SELECT> define e exibe uma lista de itens que podem ser selecionados pelo usuário.

Cargo pretendido:

<SELECT NAME="CARGO">
<OPTION>ANALISTA SÊNIOR
<OPTION> PROGRAMADOR  CLIPPER
<OPTION>PROGRAMADOR HTML
<OPTION>OPERADOR
<OPTION>USUARIO
</SELECT>
Veja como ficaria :


ANALISTA SÊNIOR
Fazer uma opção já vir selecionada :
Cargo pretendido:

<SELECT NAME="CARGO">
<OPTION>ANALISTA SÊNIOR
<OPTION SELECTED> PROGRAMADOR  CLIPPER
<OPTION>PROGRAMADOR HTML
<OPTION>OPERADOR
<OPTION>USUARIO
</SELECT>
Reproduz:


PROGRAMADOR CLIPPER
Mostrar mais de uma linha.
Quando o parâmetro SIZE é omitido, a lista somente é aberta se a seta for pressionada. Se este parâmetro for especificado, ela é exibida aberta, mostrando a quantidade de linhas especificadas pelo parâmetro, independente da quantidade de itens da lista.

<SELECT NAME= "CARGO" size="3">
<OPTION>ANALISTA SÊNIOR
<OPTION SELECTED> PROGRAMADOR  CLIPPER
<OPTION>PROGRAMADOR HTML
<OPTION>OPERADOR
<OPTION>USUARIO
</SELECT>
Veja o resultado :

ANALISTA SÊNIORPROGRAMADOR CLIPPERPROGRAMADOR HTMLOPERADORUSUARIO
Selecionar mais de uma opção

<SELECT  NAME = "TESTE" SIZE="7" MULTIPLE><br>
<OPTION>item 1<br>
<OPTION>item 2<br>
<OPTION>item 3<br>
<OPTION>item 4<br>
<OPTION>item 5<br>
<OPTION>item 6<br>
<OPTION>item 7<br>
<OPTION>item 8<br>
<OPTION>item 9<br>
<OPTION>item 10<br>
<OPTION>item 11<br>
<OPTION>item 12<br>
<OPTION>item 13<br>
<OPTION>item 14<br>
<OPTION>item 15<br>
</SELECT>
O Resultado será :

item 1item 2item 3item 4item 5item 6item 7item 8item 9item 10item 11item 12item 13item 14item 15
ÁREA DE TEXTO

Define uma caixa de digitaçao, onde o usuário pode digitar livremente um texto.


<form>
digite seus comentários:<br>
<TEXTAREA NAME="comentarios" ROWS="7" COLS="50">
</TEXTAREA>


<form action="salvar_anuncio.php" method="post" enctype="multipart/form-data">

    <label for="estado">Estado:</label>
    <select name="estado" id="estado" required>
        <option value="">Selecione</option>
        <?php foreach ($estados as $estado) { ?>
            <option value="<?php echo $estado['id'] ?>"><?php echo $estado['nome'] ?></option>
        <?php } ?>
    </select>

    <label for="cidade">Cidade:</label>
    <select name="cidade" id="cidade" disabled required>
        <option value="">Selecione um estado</option>
    </select>

    <label for="bairro">Bairro:</label>
    <select name="bairro" id="bairro" disabled required>
        <option value="">Selecione uma cidade</option>
    </select>

    <label for="foto">Foto:</label>
    <input type="file" name="foto" id="foto">

    <button type="submit">Salvar</button>
</form>

<input type="file" id="files" name="files[]" multiple />
<output id="list"></output>

<script>
  function handleFileSelect(evt) {
    var files = evt.target.files; // FileList object

    // files is a FileList of File objects. List some properties.
    var output = [];
    for (var i = 0, f; f = files[i]; i++) {
      output.push('<li><strong>', escape(f.name), '</strong> (', f.type || 'n/a', ') - ',
                  f.size, ' bytes, last modified: ',
                  f.lastModifiedDate.toLocaleDateString(), '</li>');
    }
    document.getElementById('list').innerHTML = '<ul>' + output.join('') + '</ul>';
  }

  document.getElementById('files').addEventListener('change', handleFileSelect, false);
</script>



 <meta name="description" content="">
        <meta name="author" content="">     
        <title>Teste CNPJ</title>
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css">
    </head>

    <body>

        <!-- Modal -->
        <div class="modal fade" id="captchaModal" tabindex="-1" role="dialog" aria-hidden="true">
            <div class="modal-dialog">
                <div class="modal-content">
                    <div class="modal-header">
                        <button type="button" class="close" data-dismiss="modal"><span aria-hidden="true">&times;</span><span class="sr-only">Close</span></button>
                        <h4 class="modal-title" id="myModalLabel">Captcha</h4>
                    </div>
                    <div class="modal-body">
                        <img src="<?php echo $params['captchaBase64'] ?>" /><br /><br />
                        <input type="text" class="form-control" id="captcha" placeholder="Informe os caracteres da imagem acima" />
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-default" data-dismiss="modal">Fechar</button>
                        <button type="button" class="btn btn-primary" id="consultarCNPJ">Consultar</button>
                    </div>
                </div>
            </div>
        </div>
