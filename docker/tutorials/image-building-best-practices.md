---
title: 'Esercitazione su Docker - Parte 9: Livelli delle immagini'
description: Come esaminare e gestire i livelli immagine nelle immagini Docker.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 495e1cedbcecef549102fd279ced077d096c2616
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334438"
---
# <a name="image-layering"></a>Livelli delle immagini

Si è a sapere che cosa costituisce un'immagine? Usando il comando , è possibile visualizzare il comando usato per creare ogni livello all'interno `docker image history` di un'immagine.

1. Usare il `docker image history` comando per visualizzare i livelli `getting-started` nell'immagine creata in precedenza nell'esercitazione.

    ```bash
    docker image history getting-started
    ```

    Si dovrebbe ottenere un output simile al seguente (date/ID possono essere diversi).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    Ognuna delle linee rappresenta un livello nell'immagine. La visualizzazione mostra la base nella parte inferiore con il livello più recente nella parte superiore. In questo modo è anche possibile visualizzare rapidamente le dimensioni di ogni livello, consentendo di diagnosticare immagini di grandi dimensioni.

1. Si noterà che alcune righe vengono troncate. Se si aggiunge il flag , si otterrà l'output completo ( sì, si usa un flag troncato per ottenere un `--no-trunc` output nontruncated).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Memorizzazione nella cache a livello

Dopo aver visto i livelli in azione, è disponibile una lezione importante per imparare a ridurre i tempi di compilazione per le immagini del contenitore.

> Dopo la modifica di un livello, è necessario ricreare anche tutti i livelli downstream

Diamo un'occhiata al Dockerfile che hai ancora una volta...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Tornando all'output della cronologia delle immagini, si può vedere che ogni comando nel Dockerfile diventa un nuovo livello nell'immagine. È possibile ricordare che quando è stata apportata una modifica all'immagine, le dipendenze yarn dovevano essere reinstallate. Esiste un modo per risolvere il problema? Non ha molto senso compilare le stesse dipendenze ogni volta che si compila, vero?

Per risolvere questo problema, è possibile ristrutturare il Dockerfile per supportare la memorizzazione nella cache delle dipendenze. Per le applicazioni basate su Node, tali dipendenze sono definite nel `package.json` file . Quindi, cosa succede se prima si copia solo il file in , si installano le dipendenze e quindi si *copiano* tutti gli altri file? Quindi, si ricreano le dipendenze yarn solo se è stata apportata una modifica a `package.json` . Sensato?

1. Aggiornare il Dockerfile per copiare il primo, installare `package.json` le dipendenze e quindi copiare tutti gli altri elementi in .

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Compilare una nuova immagine usando `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    Verrà visualizzato un output simile al seguente...

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    Si noti che tutti i livelli sono stati ricompilati. Perfettamente corretto, poiché il Dockerfile è stato modificato leggermente.

1. A questo punto, apportare una modifica al file , ad esempio `src/static/index.html` modificare `<title>` per pronunciare "The Awesome Todo App".

1. Compilare l'immagine Docker ora usando `docker build` di nuovo . Questa volta, l'output dovrebbe essere leggermente diverso.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    Prima di tutto, si noterà che la compilazione è stata molto più veloce. Come si può vedere, i passaggi da 1 a 4 hanno tutti `Using cache` . Quindi, hooray! Si sta usando la cache di compilazione. Anche il push e il pull di questa immagine e degli aggiornamenti saranno molto più veloci. Evviva!

## <a name="multi-stage-builds"></a>Compilazioni in più fasi

Anche se questa esercitazione non verrà illustrata in modo approfondito, le compilazioni in più fasi sono uno strumento estremamente potente che consente di usare più fasi per creare un'immagine. Esistono diversi vantaggi:

- Separare le dipendenze in fase di compilazione dalle dipendenze di runtime
- Ridurre le dimensioni complessive dell'immagine *spedendo* solo le informazioni necessarie per l'esecuzione dell'app

### <a name="maventomcat-example"></a>Esempio di Maven/Tomcat

Quando si compilano applicazioni basate su Java, è necessario un JDK per compilare il codice sorgente in bytecode Java. Tuttavia, questo JDK non è necessario nell'ambiente di produzione. È anche possibile che si utilizzino strumenti come Maven o Gradle per facilitare la compilazione dell'app.
Anche questi non sono necessari nell'immagine finale. Supporto per compilazioni in più fasi.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

Questo esempio usa una fase (denominata `build` ) per eseguire la compilazione Java effettiva usando Maven. La seconda fase (a partire `FROM tomcat` da ) copia i file dalla fase `build` . L'immagine finale è solo l'ultima fase in fase di creazione (che può essere sostituita usando il `--target` flag ).

### <a name="react-example"></a>React esempio

Quando si compilano React, è necessario un ambiente Node per compilare il codice JS (in genere JSX), i fogli di stile SASS e altro ancora in html statico, JS e CSS. Se non si esegue il rendering lato server, non è necessario nemmeno un ambiente Node per la build di produzione. Perché non spedire le risorse statiche in un contenitore nginx statico?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

In questo caso si usa un'immagine per eseguire la compilazione (ottimizzando la memorizzazione nella cache del livello) e quindi copiare `node:12` l'output in un contenitore nginx. Cool, cool?

## <a name="recap"></a>Riepilogo

Comprendendo un po' come sono strutturate le immagini, è possibile creare immagini più velocemente e compilare meno modifiche. Le compilazioni in più fasi consentono anche di ridurre le dimensioni complessive dell'immagine e di aumentare la sicurezza finale del contenitore separando le dipendenze in fase di compilazione dalle dipendenze di runtime.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Distribuzione nel cloud](deploy-to-cloud.md)