<title>Previsão do Tempo</title>

  <!-- shortcut icon -->
  <link rel="shortcut icon" href="img/temperature.png">
  <!-- Bootstrap -->
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/css/font-awesome.min.css">
  <!-- Ionicons -->
  <link rel="stylesheet" href="https://code.ionicframework.com/ionicons/2.0.1/css/ionicons.min.css">
  <!-- Theme style -->
  <link rel="stylesheet" href="dist/css/AdminLTE.min.css">
  <!-- AdminLTE Skins. Choose a skin from the css/skins
  folder instead of downloading all of them to reduce the load. -->
  <link rel="stylesheet" href="dist/css/skins/_all-skins.min.css">
  <!-- Style -->
  <link rel="stylesheet" href="css/style.css">
  <!-- Angular -->
  <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.0-rc.1/angular.min.js"></script>
  <!-- Modulos Angular -->
  <script type="text/javascript" src="app/app.module.js"></script>

  <!-- HTML5 Shim and Respond.js IE8 support of HTML5 elements and media queries -->
  <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
  <!--[if lt IE 9]>
  <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.2/html5shiv.js"></script>
  <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
  <![endif]-->
</head>
<body class="hold-transition skin-blue layout-top-nav" ng-app="minhaPrevisao">
  <!-- Cabeçalho -->
  <div class="wrapper">
    <div class="main-header">
      <div class="navbar navbar-static-top">
        <div class="container">
          <div class="navbar-header">
            <a href="#" class="navbar-brand">Previsão do Tempo</a>
          </div>
        </div>
      </div>
    </div>

    <div class="content-wrapper fundo" ng-controller="myCtrlTemp">
      <div class="container">
        <!-- Título -->
        <div class="row">
          <div class="col-md-12">
            <h4>Consulte a previsão do tempo desta semana:<strong> {{cidadeAtual +" - "+estadoAtual}}</strong></h4>
          </div>
        </div>
      </div><!-- Fim Título -->

      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <div class="box box-info corFundo"> <!-- Box Cidade e Estado -->
              <div class="box-header with-border">
                <!-- Box-tools -->
                <div class="box-tools pull-right">
                  <button class="btn btn-box-tool" data-widget="collapse"><i class="fa fa-minus"></i></button>
                  <button class="btn btn-box-tool" data-widget="remove"><i class="fa fa-times"></i></button>
                </div><!-- /.box-tools -->
                <h5 class="box-title"><strong>Informe a cidade e estado</strong></h5>
              </div><!-- /.box-header -->

              <div class="box-body corFundo">
                <div class="row">
                  <!-- Estado -->
                  <div class="col-md-4 col-sm6 col-xs-12">
                    <div class="form-group">
                      <label>Estado</label>
                      <select id="estado" class="form-control select2" style="width: 100%;" ng-model="estado"></select>
                    </div>
                  </div><!-- /.box-body -->

                  <!-- Cidade -->
                  <div class="col-md-4 col-sm6 col-xs-12">
                    <label>Cidade</label>
                    <select id="cidade" class="form-control select2" style="width: 100%;" ng-model="cidade"></select>
                  </div>

                  <!-- Botões -->
                  <div class="col-md-4 col-sm6 col-xs-12">
                    <center><div class="button">
                      <!-- Botão Consultar -->
                      <a class="btn btn-app" ng-click="consultaPrevisao()">
                        <i class="glyphicon glyphicon-search"></i>
                        Consultar
                      </a>

                      <!-- Botão favoritos     -->
                      <a class="btn btn-app" ng-click="salvaFavorito(cidade,estado)">
                        <i class="glyphicon glyphicon-star-empty"></i>
                        Favorito
                      </a>
                    </div></center>
                  </div>
                </div>
              </div>
            </div><!-- Fim Box Cidade e Estado -->
          </div> <!-- col-md-12 -->
        </div> <!-- Fim row -->
      </div> <!-- Fim container-->

      <div class="container">
        <div class="row">
          <div class="col-md-12 col-sm6 col-xs-12">
            <div class="box box-info corFundo"><!--  Box dias da Semana -->
              <div class="box-header with-border">
                <div class="box-tools pull-right">
                  <button class="btn btn-box-tool" data-widget="collapse"><i class="fa fa-minus"></i></button>
                  <button class="btn btn-box-tool" data-widget="remove"><i class="fa fa-times"></i></button>
                </div><!-- /.box-tools -->
                <h5 class="box-title"><strong>Dias da Semana</strong></h5>
              </div>
              <div class="box-body corFundo"><!-- Hoje -->
                <div class="row">
                  <div class="col-md-4 col-sm6 col-xs-12">
                    <div class="box box-widget widget-user">
                      <div class="widget-user-header bg-aqua-active">
                        <h3 class="widget-user-username" ng-bind="myData.previsoes[0].data"></h3>
                      </div>
                      <div class="widget-user-image">
                        <img class="img-circle" ng-src="{{myData.previsoes[0].imagem}}" ng-model="selectedImg">
                      </div>
                      <div class="box-footer temp-color" >
                        <div class="row">
                          <div class="col-sm-6 border-right">
                            <div class="description-block" >
                              <h5 class="description-header">Mínima</h5>
                              <span ng-bind="myData.previsoes[0].temperatura_min +' °'" class="description-text"></span>
                            </div><!-- /.description-block -->
                          </div><!-- /.col -->
                          <div class="col-sm-6 border-right">
                            <div class="description-block">
                              <h5 class="description-header">Máxima</h5>
                              <span ng-bind="myData.previsoes[0].temperatura_max +' °'" class="description-text"></span>
                            </div><!-- /.description-block -->
                          </div><!-- /.col -->
                        </div><!-- /.row -->
                      </div>
                      <div class="overlay"  ng-hide="carregando"><!--  Carregando -->
                        <i class="fa fa-refresh fa-spin"></i>
                      </div>
                    </div>
                  </div>

                  <!-- Proximo dia 1 -->
                  <div class="col-md-2 col-sm6 col-xs-12">
                    <div class="box box-widget widget-user">
                      <div class="widget-user-header bg-aqua-active">
                        <h6 ng-bind="myData.previsoes[1].data"></h6>
                      </div>
                      <div class="widget-user-image">
                        <img class="img-circle" ng-src="{{myData.previsoes[1].imagem}}" ng-model="selectedImg">
                      </div>
                      <div class="box-footer temp-color">
                        <div class="row">
                          <div class="col-sm-6 border-right">
                            <div class="description-block">
                              <h5 class="description-header">Mínima</h5>
                              <span ng-bind="myData.previsoes[1].temperatura_min +' °'" class="description-text"></span>
                            </div><!-- /.description-block -->
                          </div><!-- /.col -->
                          <div class="col-sm-6 border-right">
                            <div class="description-block">
                              <h5 class="description-header">Máxima</h5>
                              <span ng-bind="myData.previsoes[1].temperatura_max +' °'" class="description-text"></span>
                            </div><!-- /.description-block -->
                          </div><!-- /.col -->
                        </div><!-- /.row -->
                      </div>
                      <div class="overlay" ng-hide="carregando"><!--  Carregando -->
                        <i class="fa fa-refresh fa-spin"></i>
                      </div>
                    </div>
                  </div>
                  <!-- Fim Proximo dia 1 -->

                  <!-- Proximo dia 2 -->
                  <div class="col-md-2 col-sm6 col-xs-12">
                    <div class="box box-widget widget-user">
                      <div class="widget-user-header bg-aqua-active">
                        <h6 ng-bind="myData.previsoes[2].data"></h6>
                      </div>
                      <div class="widget-user-image">
                        <img class="img-circle" ng-src="{{myData.previsoes[2].imagem}}" ng-model="selectedImg">
                      </div>
                      <div class="box-footer temp-color">
                        <div class="row">
                          <div class="col-sm-6 border-right">
                            <div class="description-block">
                              <h5 class="description-header">Mínima</h5>
                              <span ng-bind="myData.previsoes[2].temperatura_min +' °'" class="description-text"></span>
                            </div><!-- /.description-block -->
                          </div><!-- /.col -->
                          <div class="col-sm-6 border-right">
                            <div class="description-block">
                              <h5 class="description-header">Máxima</h5>
                              <span ng-bind="myData.previsoes[2].temperatura_max +' °'" class="description-text"></span>
                            </div><!-- /.description-block -->
                          </div><!-- /.col -->
                        </div><!-- /.row -->
                      </div>
                      <div class="overlay" ng-hide="carregando"><!--  Carregando -->
                        <i class="fa fa-refresh fa-spin"></i>
                      </div>
                    </div>
                  </div>
                  <!-- Fim proximo dia 2 -->

                  <!-- Proximo dia 3 -->
                  <div class="col-md-2 col-sm6 col-xs-12">
                    <div class="box box-widget widget-user">
                      <div class="widget-user-header bg-aqua-active">
                        <h6 ng-bind="myData.previsoes[3].data"></h6>
                      </div>
                      <div class="widget-user-image">
                        <img class="img-circle" ng-src="{{myData.previsoes[3].imagem}}" ng-model="selectedImg">
                      </div>
                      <div class="box-footer temp-color">
                        <div class="row">
                          <div class="col-sm-6 border-right">
                            <div class="description-block">
                              <h5 class="description-header">Mínima</h5>
                              <span ng-bind="myData.previsoes[3].temperatura_min +' °'" class="description-text"></span>
                            </div><!-- /.description-block -->
                          </div><!-- /.col -->
                          <div class="col-sm-6 border-right">
                            <div class="description-block">
                              <h5 class="description-header">Máxima</h5>
                              <span ng-bind="myData.previsoes[3].temperatura_max +' °'" class="description-text"></span>
                            </div><!-- /.description-block -->
                          </div><!-- /.col -->
                        </div><!-- /.row -->
                      </div>
                      <div class="overlay" ng-hide="carregando"><!--  Carregando -->
                        <i class="fa fa-refresh fa-spin"></i>
                      </div>
                    </div>
                  </div>
                  <!-- Fim proximo dia 3 -->

                  <!-- Proximo dia 4 -->
                  <div class="col-md-2 col-sm6 col-xs-12">
                    <div class="box box-widget widget-user">
                      <div class="widget-user-header bg-aqua-active">
                        <h6 ng-bind="myData.previsoes[4].data"></h6>
                      </div>
                      <div class="widget-user-image">
                        <img class="img-circle" ng-src="{{myData.previsoes[4].imagem}}" ng-model="selectedImg">
                      </div>
                      <div class="box-footer temp-color">
                        <div class="row">
                          <div class="col-sm-6 border-right">
                            <div class="description-block">
                              <h5 class="description-header">Mínima</h5>
                              <span ng-bind="myData.previsoes[4].temperatura_min +' °'" class="description-text"></span>
                            </div><!-- /.description-block -->
                          </div><!-- /.col -->
                          <div class="col-sm-6 border-right">
                            <div class="description-block">
                              <h5 class="description-header">Máxima</h5>
                              <span ng-bind="myData.previsoes[4].temperatura_max +' °'" class="description-text"></span>
                            </div><!-- /.description-block -->
                          </div><!-- /.col -->
                        </div><!-- /.row -->
                      </div>
                      <div class="overlay" ng-hide="carregando"><!--  Carregando -->
                        <i class="fa fa-refresh fa-spin"></i>
                      </div>
                    </div>
                  </div>
                  <!-- Fim proximo dia 4 -->
                </div>
              </div><!--Fim Hoje -->
            </div>
          </div>

          <div class="col-md-4 col-sm6 col-xs-12"><!-- Box Recomendações -->
            <div class="box box-info corFundo">
              <div class="box-header with-border">
                <h5 class="box-title"><strong>Temperatura</strong></h5>
                <h4>Máxima e Mínima</h4>
                <div class="box-tools pull-right">
                  <button class="btn btn-box-tool" data-widget="collapse"><i class="fa fa-minus"></i></button>
                  <button class="btn btn-box-tool" data-widget="remove"><i class="fa fa-times"></i></button>
                </div><!-- /.box-tools -->
              </div><!-- /.box-header -->
              <div class="box-body corFundo">
                <!-- Máximo -->
                <div class="info-box">
                  <span class="info-box-icon bg-red">
                    <i class="fa fa-fw fa-arrow-up"></i>
                  </span>
                  <div class="info-box-content">
                    <span class="info-box-text"><strong>Máxima</strong></span>
                    <span class="info-box-text">{{max +' º'}}</span>
                    <span class="info-box-text"><strong>Data</strong></span>
                    <span class="info-box-text">{{dtMax}}</span>
                  </div>
                </div>
                <!-- Mínimo -->
                <div class="info-box">
                  <span class="info-box-icon bg-aqua">
                    <i class="fa fa-fw fa-arrow-down"></i>
                  </span>
                  <div class="info-box-content">
                    <span class="info-box-text"><strong>Mínima</strong></span>
                    <span class="info-box-text">{{min +' º'}}</span>
                    <span class="info-box-text"><strong>Data</strong></span>
                    <span class="info-box-text">{{dtMin}}</span>
                  </div>
                </div>
              </div>
              <div class="overlay" ng-hide="carregando"><!--  Carregando -->
                <i class="fa fa-refresh fa-spin"></i>
              </div>
            </div>
          </div><!-- Fim Box Recomendações -->

          <div class="col-md-4 col-sm6 col-xs-12"><!-- Box Recomendações -->
            <div class="box box-info corFundo">
              <div class="box-header with-border">
                <h5 class="box-title"><strong>Recomendações</strong></h5>
                <div class="box-tools pull-right">
                  <button class="btn btn-box-tool" data-widget="collapse"><i class="fa fa-minus"></i></button>
                  <button class="btn btn-box-tool" data-widget="remove"><i class="fa fa-times"></i></button>
                </div><!-- /.box-tools -->
              </div><!-- /.box-header -->
              <div class="box-body">
                <!-- Recomendação positivo -->
                <div ng-show="recomendacaoPositivo">
                  <h4>Recomendação de praia positiva</h4>
                  <h5>A temperatura para final de semana está acima de 25 º</h5>
                  <center>
                    <img class="img-circle" src="img/positivo.jpg" />
                  </center>
                </div>
                <!-- Recomendação Negativo -->
                <div ng-show="recomendacaoNegativo">
                  <h4>Recomendação de praia negativa</h4>
                  <h5>A temperatura para final de semana está abaixo de 25 º</h5>
                  <div class="widget-user-image">
                    <center>
                      <img class="img-circle" src="img/negativo.jpg" />
                    </center>
                  </div>
                </div>
                <!-- Sem recomendação -->
                <div ng-show="semFinal">
                  <h4>Recomendação de praia negativa</h4>
                  <h5>Não houve final de semana nos próximos dias</h5>
                  <div class="widget-user-image">
                    <center>
                      <img class="img-circle" src="img/semprevisao.png" />
                    </center>
                  </div>
                </div>
              </div><!-- /.box-body -->
              <div class="overlay" ng-hide="carregando"><!--  Carregando -->
                <i class="fa fa-refresh fa-spin"></i>
              </div>
            </div>
          </div><!-- Fim Box Recomendações -->

          <div class="col-md-4 col-sm6 col-xs-12"><!-- Box Gráfico -->
            <div class="box box-info corFundo">
              <div class="box-header with-border">
                <h5 class="box-title"><strong>Gráfico de variação de Temperatura</strong></h5>

                <div class="box-tools pull-right">
                  <button class="btn btn-box-tool" data-widget="collapse"><i class="fa fa-minus"></i></button>
                  <button class="btn btn-box-tool" data-widget="remove"><i class="fa fa-times"></i></button>
                </div><!-- /.box-tools -->

              </div><!-- /.box-header -->
              <div class="box-body">
                <div class="chart">
                  <canvas id="areaChart" style="height:250px"></canvas>
                </div>
              </div><!-- /.box-body -->
              <div class="overlay" ng-hide="carregando"><!--  Carregando -->
                <i class="fa fa-refresh fa-spin"></i>
              </div>
            </div>
          </div><!-- Fim Box Gráfico -->
        </div>

        <div class="modal fade bs-example-modal-sm" id="myModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel">
          <div class="modal-dialog" role="document">
            <div class="modal-content">
              <div class="modal-header fundoMsg">
                <button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
                <h4 class="tituloPrevisaoMsg"><strong>Previsão do Tempo<strong></h4>
              </div>
              <div class="modal-body colorMsg">
                <h5>{{msg}}</h5>
              </div>
              <div class="modal-footer fundoMsg">
                <button type="button" class="btn btn-ok btn-success" data-dismiss="modal">OK</button>
              </div>
            </div>
          </div>
        </div>

        <footer class="main-footer">
          <div class="container">
            Visite <a href="http://developers.agenciaideias.com.br/tempo">API Previsão do Tempo</a> para mais informações sobre o plugin.
          </div><!-- /.container -->
        </footer>

        <!-- jQuery 2.1.4 -->
        <script src="plugins/jQuery/jQuery-2.1.4.min.js"></script>
        <!-- Bootstrap 3.3.5 -->
        <script src="bootstrap/js/bootstrap.min.js"></script>
        <!-- SlimScroll -->
        <script src="plugins/slimScroll/jquery.slimscroll.min.js"></script>
        <!-- FastClick -->
        <script src="plugins/fastclick/fastclick.min.js"></script>
        <!-- AdminLTE App -->
        <script src="dist/js/app.min.js"></script>
        <!-- AdminLTE for demo purposes -->
        <script src="dist/js/demo.js"></script>
        <!-- Include all compiled plugins (below), or include individual files as needed -->
        <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js"></script>
        <!-- ChartJS 1.0.1 -->
        <script src="plugins/chartjs/Chart.min.js"></script>
        <!-- Cidades Estados -->
        <script type="text/javascript" src="app/components/cidades-estados-1.4-utf8.js"></script>
        <script type="text/javascript" src="app/components/cidadesEstados.js"></script>
      </body>
      </html>
      corFundo{
  background-color: ghostwhite;
}

.temp-color{
  background-color: paleturquoise;
}

.button{
  padding-top: 3%;
}

.fundoMsg{
  background-color: paleturquoise;
}

.colorMsg{
  background-color: #D1EEEE;
}
