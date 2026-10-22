# E1 | Albergues

## Como usar este proxecto

  1. Clona este proxecto e crea o arquivo de variables de entorno seguindo o esquema proporcionado en  *.env.example*

    
     
     ```git clone git@github.com:ilensf/e1-albergues.git```

     ```cp .env.example .env```
  2. Edita o arquivo de variables para usar credenciais reais
  3. Levanta o contedor docker
     
     ``` docker compose up -d ```

  4. Accede a Adminer a través do teu navegador web en *http://localhost:8080*. O servidor por defecto xa será db.
     O usuario e o contrasinal serán os que definiches no teu ficheiro .env

# Proba de persistencia

 | Paso | Comando | Resultado obtido |
| :--- | :---: | ---: |
| 1 | docker compose up -d | Arranca o contedor. Créase a base de datos e execútanse os scripts, engadindo os datos.|
| 2| Inserir un albergue novo desde Adminer | Insértase un novo albergue na táboa correctamente. |
| 3 | docker compose down e docker compose up -d | Paramos e eliminamos os contedores. Ao volver a iniciar, o albergue insertado previamente segue aí. |
| 4 | docker compose down -v e docker compose up -d | Paramos e eliminamos os contedores e os volumes (-v). Ao iniciar, na base de datos só estarán os datos orixinais do script |

## Por que no paso 4 o resultado é distinto?

Porque ao usar o parámetro *-v* ao facer o *docker compose down*, estamos indicando que tamén queremos eliminar os volumes, polo que ao iniciar de novo terá que crearse novamente
un volume completamente distinto, no cal non estarán os datos inseridos manualmente no paso 2.
