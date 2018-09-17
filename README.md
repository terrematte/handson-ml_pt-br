Notebooks sobre Aprendizagem de Máquina
==========================

Contribuição ao projeto de fundamentos de Aprendizagem de Máquina em python: https://github.com/ageron/handson-ml 

Aqui encontramos exemplos de códigos e as soluções Do exercício do livro O'Reilly 
[Hands-on Machine Learning with Scikit-Learn and TensorFlow](http://shop.oreilly.com/product/0636920052289.do):

[![book](http://akamaicovers.oreilly.com/images/0636920052289/cat.gif)](http://shop.oreilly.com/product/0636920052289.do)
Abra os Notebooks [Jupyter] (http://jupyter.org/) que te interesse:

* Através do [jupyter.org's notebook viewer](http://nbviewer.jupyter.org/github/ageron/handson-ml/blob/master/index.ipynb)
    * note: [github.com's notebook viewer](https://github.com/ageron/handson-ml/blob/master/index.ipynb) também funciona, mas é mais lento e as fórmulas matemáticas não são exibidas corretamente,
* ou clonando este repositório e executando o Jupyter localmente. Esta opção permite brincar com o código. Neste caso, siga as instruções de instalação abaixo.

# Instalação

Primeiro, você precisará instalar o [git] (https://git-scm.com/), se você não o tiver já.

Em seguida, clone este repositório abrindo um terminal e digitando os seguintes comandos:
    $ cd $HOME  # ou qualquer outro diretório de desenvolvimento que você preferir
    $ git clone https://github.com/ageron/handson-ml.git
    $ cd handson-ml

Se você não deseja instalar o git, você pode fazer o download de [master.zip](https://github.com/ageron/handson-ml/archive/master.zip), descompactá-lo, renomear o diretório para `handson -ml` e mova-o para o seu diretório de desenvolvimento.

Se você quiser passar pelo capítulo 16 sobre Aprendizagem por Reforço, você precisará [instalar o OpenAI gym](https://gym.openai.com/docs) e suas dependências para as simulações do Atari.

Se você está familiarizado com o Python e sabe como instalar bibliotecas Python, vá em frente e instale as bibliotecas listadas em `requirements.txt` e vá para a seção [Iniciando com Jupyter](#iniciando-com-jupyter). Se você precisar de instruções detalhadas, por favor, continue a ler.

## Python & Bibliotecas

Claro, você obviamente precisa do Python. O Python 2 já está pré-instalado na maioria dos sistemas hoje em dia, e às vezes até mesmo no Python 3. Você pode verificar qual (is) versão (ões) possui, digitando os seguintes comandos:

    $ python --version   # para Python 2
    $ python3 --version  # para Python 3

Qualquer versão do Python 3 deve estar bem, de preferência ≥ 3,5. Se você não tem o Python 3, eu recomendo instalá-lo (o Python ≥2.6 deve funcionar, mas ele está obsoleto, então o Python 3 é preferível). Para fazer isso, você tem várias opções: no Windows ou no MacOSX, basta fazer o download em [python.org] (https://www.python.org/downloads/). No MacOSX, você pode alternativamente usar [MacPorts](https://www.macports.org/) ou [Homebrew](https://brew.sh/). Se você estiver usando o Python 3.6 no MacOSX, você precisa executar o seguinte comando para instalar o pacote `certifi`, pois o Python 3.6 no MacOSX não possui certificados para validar conexões SSL (veja esta pergunta no [StackOverflow](https://stackoverflow.com/questions/27835619/urllib-and-ssl-certificate-verify-failed-error)):

    $ /Applications/Python\ 3.6/Install\ Certificates.command

No Linux, a menos que você saiba o que está fazendo, você deve usar o sistema de pacotes do seu sistema. Por exemplo, no Debian ou no Ubuntu, digite:

    $ sudo apt-get update
    $ sudo apt-get install python3

Outra opção é baixar e instalar o [Anaconda](https://www.continuum.io/downloads). Este é um pacote que inclui o Python e muitas bibliotecas científicas. Você deve preferir a versão do Python 3.

Se você escolher usar o Anaconda, leia a próxima seção, ou então pule para a seção [Usando pip](#usando-pip).

## Usando Anaconda

Ao usar o Anaconda, você pode criar opcionalmente um ambiente Python isolado dedicado a este projeto. Isso é recomendado, pois permite ter um ambiente diferente para cada projeto (por exemplo, um para este projeto), com bibliotecas e versões de bibliotecas potencialmente diferentes:

    $ conda create -n mlbook python=3.5 anaconda
    $ source activate mlbook

Isso cria um novo ambiente do Python 3.5 chamado `mlbook` (você pode alterar o nome se quiser) e o ativa. Este ambiente contém todas as bibliotecas científicas que acompanham o Anaconda. Isso inclui todas as bibliotecas que precisaremos (NumPy, Matplotlib, Pandas, Jupyter e alguns outros), exceto o TensorFlow, então vamos instalá-lo:

    $ conda install -n mlbook -c conda-forge tensorflow

Isso instala a versão mais recente do TensorFlow disponível para o Anaconda (que geralmente não é * a versão mais recente do TensorFlow) no ambiente `mlbook` (que é obtido do repositório` conda-forge`). Se você escolheu não criar um ambiente `mlbook`, basta remover a opção` -n mlbook`.

Em seguida, você pode instalar opcionalmente as extensões Jupyter. Estes são úteis para ter bons índices nos cadernos, mas eles não são necessários.

    $ conda install -n mlbook -c conda-forge jupyter_contrib_nbextensions

Tudo certo! Em seguida, siga para a seção  [Iniciando com Jupyter](#iniciando-com-jupyter).

## Usando pip

Se você não está usando o Anaconda, você precisa instalar várias bibliotecas científicas do Python que são necessárias para este projeto, em particular o NumPy, Matplotlib, Pandas, Jupyter e TensorFlow (e alguns outros). Para isso, você pode usar o sistema de empacotamento integrado do Python, pip, ou você pode preferir usar o sistema de empacotamento do próprio sistema (se disponível, por exemplo, no Linux ou no MacOSX ao usar MacPorts ou Homebrew). A vantagem de usar o pip é que é fácil criar vários ambientes Python isolados com diferentes bibliotecas e diferentes versões de bibliotecas (por exemplo, um ambiente para cada projeto). A vantagem de usar o sistema de pacotes do seu sistema é que há menos risco de haver conflitos entre as bibliotecas do Python e os outros pacotes do seu sistema. Como tenho muitos projetos com diferentes requisitos de bibliotecas, prefiro usar pip com ambientes isolados. Além disso, os pacotes pip geralmente são os mais recentes disponíveis, enquanto o Anaconda e os pacotes do sistema geralmente ficam um pouco atrasados.

Estes são os comandos que você precisa digitar em um terminal, se você quiser usar o pip para instalar as bibliotecas necessárias. Nota: em todos os comandos a seguir, se você escolher usar o Python 2 em vez do Python 3, você deve substituir o `pip3` pelo` pip` e o `python3` pelo` python`.

Primeiro você precisa ter certeza de ter a versão mais recente do pip instalada:

    $ pip3 install --user --upgrade pip

A opção `--user` instalará a última versão do pip apenas para o usuário atual. Se você preferir instalá-lo em todo o sistema (ou seja, para todos os usuários), você deve ter direitos de administrador (por exemplo, usar `sudo pip3` em vez de` pip3` no Linux) e deve remover a opção `--user`. O mesmo vale para o comando abaixo que usa a opção `--user`.

Em seguida, você pode, opcionalmente, criar um ambiente isolado. Isso é recomendado, pois permite ter um ambiente diferente para cada projeto (por exemplo, um para este projeto), com bibliotecas potencialmente muito diferentes e versões diferentes:

    $ pip3 install --user --upgrade virtualenv
    $ virtualenv -p `which python3` env

Isto cria um novo diretório chamado `env` no diretório atual, contendo um ambiente Python isolado baseado no Python 3. Se você instalou múltiplas versões do Python 3 em seu sistema, você pode substituir ```which python3``` pelo caminho para o executável Python que você preferir usar.

Agora você deve ativar este ambiente. Você precisará executar este comando toda vez que quiser usar este ambiente.

    $ source ./env/bin/activate

No Windows, o comando é um pouco diferente:

    $ .\env\Scripts\activate

Em seguida, use pip para instalar os pacotes python necessários. Se você não estiver usando virtualenv, você deve adicionar a opção `--user` (alternativamente você pode instalar as bibliotecas em todo o sistema, mas isso provavelmente irá requerer direitos de administrador, por exemplo usando` sudo pip3` em vez de `pip3` no Linux) .

    $ pip3 install --upgrade -r requirements.txt

Ótimo! Você está pronto, você só precisa começar o Jupyter agora.

## Iniciando com Jupyter

Se você quiser usar as extensões Jupyter (opcional, elas são úteis principalmente para ter bons índices), primeiro você precisa instalá-las:

    $ jupyter contrib nbextension install --user

Em seguida, você pode ativar uma extensão, como a extensão Table of Contents (2):

    $ jupyter nbextension enable toc2/main

Ótimo! Agora você pode iniciar o Jupyter, simplesmente digite:

    $ jupyter notebook
    
Isso deve abrir o seu navegador, e você deve ver a visão em árvore do Jupyter, com o conteúdo do diretório atual. Se o seu navegador não abrir automaticamente, visite [localhost:8888](http://localhost:8888/tree). Clique em `index.ipynb` para começar!

Note: você também pode visitar [http://localhost:8888/nbextensions](http://localhost:8888/nbextensions) para ativar e configurar as extensões do Jupyter.

Parabéns! Você está pronto para aprender Machine Learning, hands on!

# Contribuidores
Gostaria de agradecer a todos que contribuíram para este projeto, seja fornecendo feedback útil, arquivando problemas ou enviando ```Pull Requests```. Agradecimentos especiais vão para Steven Bunkley e Ziembla que criaram o diretório `docker`.
