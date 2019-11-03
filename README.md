
# Composer gerenciador de dependências para PHP

https://www.udemy.com/course/composer-gerenciador-de-dependencias-para-php/

Composer é um gerenciador de dependências para PHP. Composer é usado em todas as estruturas modernas do PHP (Symfony, Laravel) e é uma das ferramentas mais recomendadas que resolve problemas fundamentais na maioria dos projetos da web. Desenvolvedores e grandes empresas já estão utilizando para gerenciar suas dependencias em projetos, se você ainda não está utilizando fique sabendo que você está ficando para trás, não perca mais tempo e faça este curso que irá ensinar a utilização passo a passo e terá um instrutor para tirar todas as dúvidas que surgir

## <a name="indice">Índice</a>

1. [Introdução](#parte1)     
2. [Primeiros passos para geração do arquivo de configuração](#parte2)     
3. [Gerando o primeiro arquivo composer.json](#parte3)     
4. [Solucionando problemas na instalação global](#parte4)     
5. [Solucionando problema de configuração no mac os](#parte5)     
6. [Configurando depêndencias no projeto](#parte6)     
7. [Baixando depêndencias para o projeto com composer](#parte7)     
8. [Aprendendo sobre require-dev, composer install e update](#parte8)     
9. [Resolvendo problema no require](#parte9)     
10. [Testando o monolog na prática](#parte10)     
11. [Adicionando phpunit no require-dev](#parte11)     
12. [Removendo pacotes](#parte12)     
13. [Entendendo versões no composer](#parte13)     
14. [Travamento de versões](#parte14)     
15. [Caminhos personalizados](#parte15)     
16. [Bônus](#parte16)     
---


## <a name="parte1">1 - Introdução</a>

- https://getcomposer.org/


[Voltar ao Índice](#indice)

---


## <a name="parte2">2 - Primeiros passos para geração do arquivo de configuração</a>



[Voltar ao Índice](#indice)

---


## <a name="parte3">3 - Gerando o primeiro arquivo composer.json </a>


```
$ composer init

```


[Voltar ao Índice](#indice)

---


## <a name="parte4">4 - Solucionando problemas na instalação global</a>



[Voltar ao Índice](#indice)

---


## <a name="parte5">5 - Solucionando problema de configuração no mac os </a>



[Voltar ao Índice](#indice)

---


## <a name="parte6">6 - Configurando depêndencias no projeto</a>



[Voltar ao Índice](#indice)

---


## <a name="parte7">7 - Baixando depêndencias para o projeto com composer </a>

```
{
    "name": "curso/projeto1",
    "description": "Projeto 1 do curso de composer",
    "require": {
        "monolog/monolog": "^2.0"
    },
    "license": "MIT",
    "authors": [
        {
            "name": "josemalcher",
            "email": "contato@josemalcher.net"
        }
    ]
}

```


[Voltar ao Índice](#indice)

---


## <a name="parte8">8 - Aprendendo sobre require-dev, composer install e update </a>

```
{
    "name": "curso/projeto1",
    "description": "Projeto 1 do curso de composer",
    "require": {
        "monolog/monolog": "^2.0"
    },
    "license": "MIT",
    "authors": [
        {
            "name": "josemalcher",
            "email": "contato@josemalcher.net"
        }
    ],
    "require": {
        "php": ">5.5.5"
    }
}

$ composer update

Key require is a duplicate in ./composer.json at line 16
Loading composer repositories with package information
Updating dependencies (including require-dev)
Package operations: 0 installs, 0 updates, 2 removals
  - Removing psr/log (1.1.0)
  - Removing monolog/monolog (2.0.0)
Writing lock file
Generating autoload files

```

[Voltar ao Índice](#indice)

---


## <a name="parte9">9 - Resolvendo problema no require </a>

```
{
    "name": "curso/projeto1",
    "description": "Projeto 1 do curso de composer",
    "require": {
        "monolog/monolog": "^2.0",
        "php": ">5.5.5"
    },
    "license": "MIT",
    "authors": [
        {
            "name": "josemalcher",
            "email": "contato@josemalcher.net"
        }
    ],
    "require-dev": {
        "phpunit/phpunit":"^7"
    }
}



```


[Voltar ao Índice](#indice)

---


## <a name="parte10">10 - Testando o monolog na prática </a>

```php
<?php

require_once './vendor/autoload.php';

use Monolog\Logger;
use Monolog\Handler\StreamHandler;
use Monolog\Handler\FirePHPHandler;

// Create the logger
$logger = new Logger('my_logger');
// Now add some handlers
$logger->pushHandler(new StreamHandler(__DIR__.'/logs/my_app.log', Logger::DEBUG));
$logger->pushHandler(new FirePHPHandler());

// You can now use your logger
$logger->info('My logger is now ready');
```

[Voltar ao Índice](#indice)

---


## <a name="parte11">11 - Adicionando phpunit no require-dev</a>



[Voltar ao Índice](#indice)

---


## <a name="parte12">12 - Removendo pacotes </a>

- composer remove aharen/pay

Ou Removendo de composer.json + composer update

[Voltar ao Índice](#indice)

---


## <a name="parte13">13 - Entendendo versões no composer </a>

- ^4.5 >= 4.5 <= 5
- ^1.22 >= 1.22 <= 22
- >2 < 3
- >5.0.*

[Voltar ao Índice](#indice)

---


## <a name="parte14">14 - Travamento de versões </a>

```
{
    "name": "curso/projeto1",
    "description": "Projeto 1 do curso de composer",
    "require": {
        "monolog/monolog": "@stable",
        "php": ">5.5.5"
    },
    "license": "MIT",
    "authors": [
        {
            "name": "josemalcher",
            "email": "contato@josemalcher.net"
        }
    ],
    "require-dev": {
        "phpunit/phpunit":"^4.3"
    }
}

```

[Voltar ao Índice](#indice)

---


## <a name="parte15">15 - Caminhos personalizados</a>

- composer update --no-dev

```
$ composer update --no-dev   
Loading composer repositories with package information
Updating dependencies
Nothing to install or update
Package operations: 0 installs, 0 updates, 22 removals
  - Removing webmozart/assert (1.5.0)
  - Removing symfony/yaml (v3.4.33)
  - Removing symfony/polyfill-ctype (v1.12.0)
  - Removing sebastian/version (1.0.6)
  - Removing sebastian/recursion-context (1.0.5)
  - Removing sebastian/global-state (1.1.1)
  - Removing sebastian/exporter (1.2.2)
  - Removing sebastian/environment (1.3.8)
  - Removing sebastian/diff (1.4.3)
  - Removing sebastian/comparator (1.2.4)
  - Removing phpunit/phpunit-mock-objects (2.3.8)
  - Removing phpunit/phpunit (4.8.36)
  - Removing phpunit/php-token-stream (1.4.12)
  - Removing phpunit/php-timer (1.0.9)
  - Removing phpunit/php-text-template (1.2.1)
  - Removing phpunit/php-file-iterator (1.4.5)
  - Removing phpunit/php-code-coverage (2.2.4)
  - Removing phpspec/prophecy (1.9.0)
  - Removing phpdocumentor/type-resolver (1.0.1)
  - Removing phpdocumentor/reflection-docblock (4.3.2)
  - Removing phpdocumentor/reflection-common (2.0.0)
  - Removing doctrine/instantiator (1.2.0)
Generating autoload files

```

```
$ composer update --no-dev
Loading composer repositories with package information
Updating dependencies
Package operations: 2 installs, 0 updates, 0 removals
  - Installing psr/log (1.1.2): Loading from cache
  - Installing monolog/monolog (2.0.0): Loading from cache
Generating autoload files
```


[Voltar ao Índice](#indice)

---


## <a name="parte16">16 - Bônus</a>



[Voltar ao Índice](#indice)

---

