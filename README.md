**UNIVERSIDADE LUSÓFONA**

# Lab 10: Portfolio II 🌤️

### Objetivo 

* Finalizar os requisitos do Lab. 9.
* Recolher todos os conteúdos necessários, organizados numa pasta e em ficheiros de texto, tal como indicado no Lab. 9.
* desenhar o diagrama entidade relação da base de dados a construir no Lab. 10


### Recomendações
* leia uma vez o enunciado. Este detalha todos os passos e fornece o código necessário, sendo rápida a sua realização.
* se tiver dúvidas, consulte os slides das aulas [[1](https://moodle.ensinolusofona.pt/draftfile.php/74319/user/draft/994903460/pw-04-django-01-23.pptx?time=1684058176856) [2](https://moodle.ensinolusofona.pt/draftfile.php/74319/user/draft/994903460/pw-04-django-02.pptx)] vídeos [[1](https://educast.fccn.pt/vod/clips/13ii54fteb/html5.html?locale=en), [2](https://educast.fccn.pt/vod/clips/1m7vvfknq2/streaming.html?locale=en)] e a documentação do [djangoproject](https://www.djangoproject.com/)
* se tiver dúvidas, consulte os slides das aulas e a documentação do [djangoproject](https://www.djangoproject.com/)
* familiarize-se e use o [glossario](https://moodle.ensinolusofona.pt/pluginfile.php/549224/mod_resource/content/4/PW_glossario_2023.pdf) que terão disponivel no exame.


## 0. Primeiros passos 👶
Trabalhe a partir do seu projeto criado no Lab 9, que está em  
1. se o tiver no computador onde odesenvolveu, basta ativar o ambiente virtual com "pipenv shell".
2. Se estiver a trabalhar no projeto noutro computador, deve 
   * instalar os modulos necessarios, com o compando `pipenv install`
   * ativar o ambiente virtual, com `pipenv shell`  

## 1. Aprimore a sua aplicação ✨
4. Este será o seu portfolio, carta de apresentação sua na internet muito valorizada no mundo do trabalho! Por isso, esmere-se, e abrir-lhe-á oportunidades de emprego muitas na medida do que se aplicar neste projeto. 
* Releia o enunciado do Lab. 8 com atenção e garanta que implementou tudo, e tem tudo a funcionar devidamente
* Esmere-se no layout, garantindo que tem um aspecto profissional e aplica tecnicas modernas de CSS.
* Várias páginas irão apresentar um conjunto de items (cadeiras, projetos, TFCs), com um titulo, imagem, texto e mais alguns atributos. Desenhe o layout destes items independentes / tipo postais, como feito no laboratório anterior lab.5. Crie elementos para cada página, com conteúdos inventados para já. 

## 2. Blog

* Implemente um blog, que permite realizar posts. 
* Siga os passos da aplicação [Tarefas](https://github.com/ULHT-PW/pw-aula-django-02/) desenvolvida na aula. [Experimente a aplicação a correr no Heroku](http://pw-aula03.herokuapp.com/). No README estão descritos todos os passos seguidos assim como um video da implementação! (incluindo a estilização CSS que não cheguei a fazer na aula por falta de tempo).
* Cada Post terá como atributos autor, data, título, descrição, e opcionalmente um link (para projeto ou página do seu portfolio) e uma imagem. 
* Explore labels, widgets e help-texts (veja exemplos [aqui](https://github.com/ULHT-PW/pw-aula-django-02/#formul%C3%A1rio)).
* Use uma única página para listar os posts e no final incluir o formulário para escrever um novo post. 
* Renderize cada post como um "postal", elemento separado como em Tarefas.


## 3. Quizz sobre programação Web

* Conceba um Quizz "programação Web" sobre o tópico, em especial abordando aspectos falados na sua secção sobre Programação Web (veja em baixo). 
* Não precisa de guardar as respostas às perguntas. Construa o formulário diretamente em HTML no HTML. Explore os vários tipos de entrada tal como sugerido no [lab 3](https://github.com/ULHT-PW/pw-lab3#3-p%C3%A1gina-com-quizz-). Recolha também o nome da pessoa que responder.
* Se for submetido um formulário através dum POST, a variável `request.POST`é um dicionário que contem a informação submetida, podendoser acedida da seguinte forma: 

```Python
def quizz(request):
   if request.method == 'POST'
      n = request.POST['nome']
      p = pontuacao_quizz(request)
      r = PontuacaoQuizz(nome=n, pontuacao=p)
      r.save()
```
* crie uma função que recebe como argumento `request` e calcula e retorna a pontuação obtida pelo participante.
* Crie no models.py uma classe PontuacaoQuizz para guardar o nome e pontuação conseguida pelas participantes no Quizz.
* na view, se o `request` for um POST chame a função para obter a cotação. Depois crie um objeto da classe PontuacaoQuizz para guardar o nome e pontuação obtido, e grave  
* crie a função `desenha_grafico_resultados` (crie-a primeiro usando um Jupyter para verificar que funciona bem, e com uma lista fictícia de resultados):
   * a função deve ir buscar à base de dados os resultados dos participantes no Quizz (`PontuacaoQuizz.objects.all()`), ordene-o decrescentemente pelas pontuações com a função `sorted` e um um `lambda`. Crie em seguida duas listas, uma de nomes e outra de pontuações
   * que crie um [gráfico de barras horizontal](https://moodle.ensinolusofona.pt/pluginfile.php/318343/mod_label/intro/pw-03-python-04-matplotlib.pdf?#page=30)) com o módulo matplotlib do Python, mostrando a pontuação no eixo dos x e nomes no eixo dos y). Para tal: 
   * [Grave](https://moodle.ensinolusofona.pt/pluginfile.php/318343/mod_label/intro/pw-03-python-04-matplotlib.pdf?#page=18) a imagem na pasta portfolio\static\images
   * apresente a imagem com o gráfico dos resultados no HTML do Quizz, no fim. 
   * Na view do quizz, depois de cada nova submissão de resposta, chame a função desenha_grafico_resultados para atualizar o gráfico. 


## 4. Portfolio no Heroku ☁
* Crie um repositório GitHub para o seu projeto
* Sincronize com o PythonAnywhere para ter a aplicação a correr.


## 5. Diagrama Entidade Relação 🛢

* Desenhe o Diagrama Entidade Relação da base de dados que precisará para guardar numa base de dados toda a informação descrita na secção **3**. Use uma ferramenta a seu gosto (por exemplo [draw.io](draw.io)). 
* Neste laboratório concentrar-se-á na modelação e só no Lab. 10 irá implementar a base de dados. Deverá identificar todas as classes, atributos e relações (1:1, 1:N e N:N).
* Para construir o DER leia com atenção os requisitos da secção 3 onde se detalham muitas das tabelas e atributos que irá ter, assim como relações.
* Este DER deverá ser apresentado 


## 6. Estrutura 🦴🦴🦴 

Eis a estrutura para a qual estamos a convergir (ainda poderá sofrer alguns ajustes)

Estrutura da aplicação:
* Home (Hero page)
* Sobre mim
   * Licenciatura
      * cadeiras 
   * Educação
      * escolas 
   * Certificados
   * Outras habilitações
   * Aptidões e competências pessoais
      * técnicas
      * organizativas
      * sociais
      * linguisticas
   * Interesses e hobbies
* projetos 
   * realizados por mim
   * Trabalhos Finais de Curso interessantes   
* Web   
   * tecnologias existentes
      * front-end
      * back-end
      * outras 
   * Sobre este website
      * estrutura do site
      * diagrama DER
      * tecnologias usadas
      * padrões usados     
   * laboratórios 
   * notícias
   * exemplos e técnicas
   * Quizz    
* Blog
* Contacto
* Rodapé

## 6. Recolha de Conteúdos 📚

* Durante esta semana deverá recolher **todo o material em baixo**. Organize-o e guarde-o num repositório GitHub. No Lab 10, após construir a base de dados, irá inserir os conteúdos. Atenção que foram adicionados mais alguns intems em relação à estrutura apresentada no Lab. 8, secção 10. Alterou-se tambem o aninhamento de Licenciatura dentro de Educação.

* **Hero Page**
  * Redija um texto de apresentação que irá colocar na pagina de entrada, HeroPage, no segundo elemento (onde o texto aparece quando fazemos scroll da Hero Page como neste [exemplo](https://codepen.io/LucioStuder/pen/vYpqwra)). Este texto poderá falar de:
    * de motivações para escolher o seu curso, 
    * daquilo que mais tem gostado de aprender no curso,
    * de espectativas do que gostaria de fazer quando acabar o curso. 
    * de hobbies

* **Educação**
   * educação, listar Formação, com campos curso, local, período logotipo da instituição
      * cursos superior
      * escolas no secundário
      * certificados
   * licenciatura, pagina que apresenta a lista de cadeiras do curso, organizada por semestre e anos. Quando clicada uma cadeira, aparece informação relativamente a: nome, ano, semestre, ECTS, ano letivo frequentado, topicos abordados, ranking de 1 a 5 estrelas (indicando se gostou ou não), professores (da classe Pessoa com campos nome e link para a sua pagina da lusofona e no linkedin), link para página da cadeira (se existir), lista de projetos realizados (classe projeto)
   * Aptidões e competências pessoais (com atributos titulo, descrição curta, lista de projetos (Projeto) realizados onde foi aplicada essa competência caso se aplique, lista de disciplinas (Disciplina) onde foi trabalhada essa competência caso se aplique)
    * [Técnicas]( https://www.e-konomista.pt/competencias-tecnicas/): 
    * linguagens de programação ou tecnologias, relatórios word, apresentações powerpoint, realização de videos, protótipos
    * [Organizativas]( https://www.e-konomista.pt/competencias-de-organizacao/)
    * [Sociais](https://www.e-konomista.pt/aptidoes-e-competencias-sociais)
    * Linguísticas. lista de linguas estrangeiras faladas, com indicação de nível (proficiente, independente ou elementar), e referencia se existir a certificação obtida ou outra explicação (lingua materna, viveu noutro país)
 * interesses (com atributos titulo, descrição, fotografia e link (e.g., clube de fotografia) 
    * outras atividades
    * desporto
    * hobbies
    * voluntariado

* **Projetos**
   * realizados por mim: lista de projetos realizados, com atributos: titulo, descrição até 500 carateres, imagem, ano de realização, cadeira (classe Cadeira, caso tenha sido projeto associado a uma cadeira), participantes (da classe Pessoa, da classe Pessoa com atributos nome e link para a sua pagina no linkedin, e link para a aplicação portfolio do projeto PW), link para repositorio GitHub, link para video no youtube, tecnologias usadas, competencias (classe Competencia)
   * trabalhos de fim de curso: lista de 6 Trabalhos finais de Curso (TFCs) de anos passados realizados por colegas seus que achou interessantes, onde TFC tem atributos: titulo, autor (multiplos), orientador (multiplos), ano de realização, sumário, resumo até 500 carateres, link para relatório, links para repositório github e vídeo no Youtube, se existentes. Será facultada uma pasta com relatórios de TFC dos últimos anos para consultar e escolher.

* **Programação Web**
   * Tecnologias: Falar das seguintes Tecnologias, com os atributos: nome (por extenso), acrónimo (caso exista, e.g., CSS para Cascade Style Sheet), ano de criação, criador, logotipo, link para site oficial, descrição das principais características. 
         * Back-end: Laravel, ASP.NET, Spring MVC, Express, Django
         * Front-end: Angular, React, Vue, Svelte
         * Outras: WordPress, OutSystems, Weebly, Wix
   * Laboratórios: página que lista links para os laboratórios realizados na disciplina de PW, com o título e descrição dos tópicos abordados
   * Notícias: listagem de 10 noticias sobre artigos do medium.com que tenha gostado, com campos: título, 3 linhas de texto, imagem e link
   * exemplos de técnicas e efeitos que gosta, sites que gosta e de sites que acha maus, tendencias modernas de programação Web, aspectos obsoletos

* **Blog**. Post tem atributos autor, data, título e descrição e eventualmente um link (para projeto, página do seu portfolio) e foto. deverá ter pelo menos 5 posts de outros colegas seus a comentar que gostaram de fazer um determinado projeto consigo, ou de certo trabalho que você fez, ou que é um bom colega para estudar

* **Sobre este website**, informação sobre este website, incluindo
   * Estrutura do website: com mapa do site
   * Descrição da base de dados e sua modelação, incluindo o DER e explicação de principais relações.
   * lista de tecnologias usadas na criação do website: HTML, CSS, Python, Django, Heroku, JavaScript). Tecnologia terá os seguintes atributos: nome (por extenso), acrónimo (caso exista, e.g., CSS para Cascade Style Sheet), ano de criação, criador, logotipo, imagem exemplificativa (excerto de código, e.g.) link para site oficial, descrição do que é e onde & como foi usado. 
   * lista de padrões usados: padrão arquitetural cliente-servidor HTTP, padrão de software MVC, padrão de comunicação assíncrona (AJAX) 
   * Comentários: para recolher opiniões sobre o seu website, avaliando 10 critérios, tal como descrito na secção acima.

* **Contacto**
   * links para a sua conta linkedin. se não tiver, crie. Adicione à sua conta de colegas seus, amigos e professores e adira a grupos de interesse na sua área (DEISI)
   * link para o seu github
   * nome da cidade onde vive
   * facebook, instagram

* **Rodapé**
   * link para Mapa do site
   * contacto
   * nome do autor
   * ano
   * universidade
   * logotipo


## 7. Submissão 🏁

submeta no formulário disponivel no Moodle:
* o link para o o repo do portfolio
* o link para o repo do material recolhido
* o link para a aplicação a correr no Heroku
