---
title: 'Esercitazione: Introduzione a Docker & Visual Studio Code'
description: Esercitazione in più passaggi che illustra le nozioni di base sull'uso di Docker con Visual Studio Code.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: tutorial
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 75a51f478e4e58700f6025dd6a87fcc38439ed87
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222656"
---
# <a name="tutorial-get-started-with-docker"></a>Esercitazione: Introduzione a Docker

Questa esercitazione illustra come creare e distribuire app Docker, incluso l'uso di più contenitori con un database e l'uso di Docker Compose. Si distribuirà anche l'app in contenitori in Azure.

## <a name="start-the-tutorial"></a>Avviare l'esercitazione

Se il comando è già stato eseguito per iniziare a usare l'esercitazione, congratulazioni.  In caso contrario, aprire un prompt dei comandi o una finestra bash ed eseguire il comando:

```cli
docker run -d -p 80:80 docker/getting-started
```

Si noteranno alcuni flag usati. Ecco altre informazioni:

- `-d` - Eseguire il contenitore in modalità scollegata (in background)
- `-p 80:80` - Eseguire il mapping della porta 80 dell'host alla porta 80 nel contenitore
- `docker/getting-started` - l'immagine da usare

> [!TIP]
> È possibile combinare flag a carattere singolo per abbreviare il comando completo.
> Ad esempio, il comando precedente potrebbe essere scritto come:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>Estensione VS Code

Prima di andare oltre, è necessario evidenziare l'estensione docker VS Code, che offre una rapida visualizzazione dei contenitori in esecuzione nel computer. Consente di accedere rapidamente ai log dei contenitori, di ottenere una shell all'interno del contenitore e di gestire facilmente il ciclo di vita del contenitore (arresto, rimozione e così via).

Per accedere all'estensione, seguire le istruzioni [riportate qui.](https://code.visualstudio.com/docs/containers/overview) Usare l'icona Docker a sinistra per aprire la visualizzazione Docker. Se si apre l'estensione ora, verrà visualizzata questa esercitazione in esecuzione. Il nome del contenitore ( `angry_taussig` di seguito) è un nome creato in modo casuale. Quindi, molto probabilmente si ha un nome diverso.

![Contenitore dell'esercitazione in esecuzione nell'estensione Docker](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Che cos'è un contenitore

Ora che è stato eseguito un contenitore, che *cos'è* un contenitore? In poche parole, un contenitore è semplicemente un altro processo nel computer isolato da tutti gli altri processi nel computer host. Questo isolamento sfrutta gli spazi dei nomi del kernel e [cgroup,](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504)le funzionalità che sono state in Linux per molto tempo. Docker ha lavorato per rendere queste funzionalità disponibili e facili da usare.

> [!NOTE]
> **Creazione di contenitori da zero** Per vedere come vengono creati i contenitori da zero, Liz Rice di Aqua Security ha un video in cui crea un contenitore da zero in Go:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Che cos'è un'immagine del contenitore

Quando si esegue un contenitore, usa un file system isolato. Questo file system personalizzato viene fornito da **un'immagine del contenitore**. Poiché l'immagine contiene il file system del contenitore, deve contenere tutto il necessario per eseguire un'applicazione, ad esempio tutte le dipendenze, la configurazione, gli script, i file binari e così via. L'immagine contiene anche altre configurazioni per il contenitore, ad esempio variabili di ambiente, un comando predefinito da eseguire e altri metadati.

Verranno approfondite le immagini in un secondo momento, con argomenti come la strating, le procedure consigliate e altro ancora.

> [!NOTE]
> Se si ha familiarità con `chroot` , si può pensare a un contenitore come a una versione estesa di `chroot` . Il file system proviene semplicemente dall'immagine. Tuttavia, un contenitore aggiunge un ulteriore isolamento non disponibile quando si usa semplicemente chroot.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Applicazione](your-application.md)
