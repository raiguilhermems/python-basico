<h1>Django</h1>

Utiliza arquitetura MVT:

Model -> camada que mapeia os BANCOS DE DADOS do projeto  
Template -> camada de APRESENTAÇÃO dos dados. COMO os dados serão mostrados  
View -> lógica de negócio. QUAIS dados serão mostrados  

Principais comandos admin:

makemigrations -> usado para manipular banco de dados  
migrate -> usado para manipular banco de dados  
runserver -> iniciar servidor  
startproject -> iniciar novo projeto  
startapp -> iniciar um novo app  


Passo a passo:  

1)Cria o app:  
python3 manage.py startapp nome_do_app  

2)Inclui o app no arquivo settings.py da raiz do projeto  
Ex:  
base.apps.BaseConfig -> esse nome é baseado no caminho para classe do arquivo apps.py do nosso novo app  

3)Crio as funções no arquivo views.py da pasta do app  
from django.shortcuts import render  
from django.http import HttpResponse  

def home(request):
    return HttpResponse('Página Inicial')


def room(request):
    return HttpResponse('ROOM')

4)Crio o arquivo urls.py na pasta do app para incluir as urls desse app

from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name= 'home'),
    path('room/', views.room, name= 'room'),
]

5)Incluo no arquivo url.py da raiz do projeto essas urls criadas
from django.contrib import admin
from django.urls import path, *include*


urlpatterns = [
    path('admin/', admin.site.urls),
    *path('', include('base.urls')),*
]




