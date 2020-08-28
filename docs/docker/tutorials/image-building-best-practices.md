---
title: 'Esercitazione su Docker-parte 8: sovrapposizione di immagini'
description: Come esaminare e gestire i livelli di immagine nelle immagini docker.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: eae21a729f30a0c77fa52e5774a2f5157286dab1
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039134"
---
# <a name="image-layering"></a>Sovrapposizione immagini

Si è appreso che è possibile vedere che cosa compone un'immagine? Utilizzando il `docker image history` comando, è possibile visualizzare il comando utilizzato per creare ogni livello all'interno di un'immagine.

1. Usare il `docker image history` comando per visualizzare i livelli nell' `getting-started` immagine creata in precedenza nell'esercitazione.

    ```bash
    docker image history getting-started
    ```

    Verrà visualizzato un output simile al seguente (le date e gli ID potrebbero essere diversi).

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

    Ognuna delle righe rappresenta un livello nell'immagine. La visualizzazione Mostra la base in basso con il livello più recente nella parte superiore. Questa operazione consente inoltre di visualizzare rapidamente le dimensioni di ogni livello, aiutando a diagnosticare immagini di grandi dimensioni.

1. Si noterà che molte righe sono troncate. Se si aggiunge il `--no-trunc` flag, si otterrà l'output completo (Sì, si userà un flag troncato per ottenere l'output non troncato).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Caching del livello

A questo punto, dopo aver esaminato i livelli in azione, è importante imparare a ridurre i tempi di compilazione per le immagini del contenitore.

> Una volta modificato un livello, è necessario ricreare anche tutti i livelli downstream

Si osservi il Dockerfile che si stava usando una sola volta...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Tornando all'output della cronologia immagini, si noterà che ogni comando in Dockerfile diventa un nuovo livello nell'immagine. È possibile ricordare che, quando è stata apportata una modifica all'immagine, le dipendenze Yarn devono essere reinstallate. Esiste un modo per risolvere il problema? Non è molto sensato fornire le stesse dipendenze ogni volta che si compila, giusto?

Per risolvere il problema, è possibile ristrutturare i Dockerfile per supportare la memorizzazione nella cache delle dipendenze. Per le applicazioni basate su nodi, tali dipendenze sono definite nel `package.json` file. Quindi, cosa accade se in primo luogo è stato copiato solo il file, si installano le dipendenze e *quindi* si copiano tutti gli altri elementi? Quindi, si ricreano solo le dipendenze Yarn se è stata apportata una modifica a `package.json` . Ha senso?

1. Aggiornare Dockerfile per copiare il `package.json` primo, installare le dipendenze e quindi copiare tutti gli altri elementi in.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Creare una nuova immagine usando `docker build` .

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

    Si noterà che tutti i livelli sono stati ricompilati. Perfettamente, dal momento che la Dockerfile è stata modificata.

1. A questo punto, apportare una modifica al `src/static/index.html` file (ad esempio, modificare `<title>` in modo da indicare "The Awesome todo app").

1. Compilare l'immagine Docker ora usando di `docker build` nuovo. Questa volta l'output dovrebbe essere leggermente diverso.

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

    Prima di tutto, si noterà che la compilazione è stata molto più rapida. Verranno visualizzati i passaggi 1-4 `Using cache` . Evviva! Si sta usando la cache di compilazione. Il push e il pull di questa immagine e gli aggiornamenti saranno molto più veloci. Evviva!

## <a name="multi-stage-builds"></a>Compilazioni in più fasi

Anche se non si intende approfondire questa esercitazione, le compilazioni in più fasi sono uno strumento incredibilmente potente che consente di usare più fasi per creare un'immagine. Sono disponibili diversi vantaggi:

- Separare le dipendenze in fase di compilazione dalle dipendenze di runtime
- Ridurre le dimensioni complessive dell'immagine spedendo *solo* ciò che l'app deve eseguire

### <a name="maventomcat-example"></a>Esempio di Maven/Tomcat

Quando si compilano applicazioni basate su Java, è necessario un JDK per compilare il codice sorgente in bytecode Java. Tuttavia, questo JDK non è necessario nell'ambiente di produzione. È anche possibile usare strumenti come Maven o Gradle per compilare l'app.
Anche questi non sono necessari nell'immagine finale. Guida alle compilazioni in più fasi.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

Questo esempio usa una fase (denominata `build` ) per eseguire la compilazione Java effettiva con Maven. La seconda fase (a partire da `FROM tomcat` ) copia i file dalla `build` fase. L'immagine finale è solo l'ultima fase creata (che può essere sottoposta a override tramite il `--target` flag).

### <a name="react-example"></a>Esempio di React

Quando si compilano applicazioni REACT, è necessario un ambiente node per compilare il codice JS (in genere JSX), i fogli di stile SASS e altro ancora in HTML, JS e CSS statici. Se non si esegue il rendering sul lato server, non è necessario un ambiente node per la compilazione di produzione. Perché non distribuire le risorse statiche in un contenitore nginx statico?

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

In questo caso si usa un' `node:12` immagine per eseguire la compilazione (massimizzazione della memorizzazione nella cache dei livelli) e quindi copiare l'output in un contenitore nginx. Interessante, eh?

## <a name="recap"></a>Riepilogo

Grazie alla comprensione di come sono strutturate le immagini, è possibile creare immagini più velocemente e fornire un numero inferiore di modifiche. Le compilazioni in più fasi consentono inoltre di ridurre le dimensioni complessive dell'immagine e di aumentare la sicurezza finale del contenitore separando le dipendenze in fase di compilazione dalle dipendenze

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Distribuzione nel cloud](deploy-to-cloud.md)