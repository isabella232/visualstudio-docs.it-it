---
title: 'Esercitazione su Docker: Introduzione a Docker'
description: Esercitazione in più passaggi che illustra le nozioni di base sull'uso di Docker con Visual Studio Code.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 9961810ad408a384db46439235b0b7acab325062
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2020
ms.locfileid: "89178339"
---
# <a name="tutorial-get-started-with-docker"></a>Esercitazione: Introduzione a Docker

Questa esercitazione illustra la creazione e la distribuzione di app Docker, tra cui l'uso di più contenitori con un database e l'uso di Docker Compose. Si distribuirà anche l'app in contenitori in Azure.

## <a name="start-the-tutorial"></a>Avviare l'esercitazione

Se è già stato eseguito il comando per iniziare l'esercitazione, congratulazioni!  In caso contrario, aprire un prompt dei comandi o una finestra bash ed eseguire il comando:

```cli
docker run -d -p 80:80 docker/getting-started
```

Si noterà che vengono usati alcuni flag. Di seguito sono riportate altre informazioni su di esse:

- `-d` -eseguire il contenitore in modalità scollegata (in background)
- `-p 80:80` -mappare la porta 80 dell'host alla porta 80 nel contenitore
- `docker/getting-started` -immagine da usare

> [!TIP]
> È possibile combinare flag a carattere singolo per abbreviare il comando completo.
> Come esempio, il comando precedente potrebbe essere scritto come segue:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>Estensione VS Code

Prima di andare troppo oltre, è opportuno evidenziare l'estensione Docker VS Code, che offre una visualizzazione rapida dei contenitori in esecuzione nel computer. Consente di accedere rapidamente ai log dei contenitori, di ottenere una shell all'interno del contenitore e di gestire facilmente il ciclo di vita del contenitore (arrestare, rimuovere e così via).

Per accedere all'estensione, seguire le istruzioni riportate [qui](https://code.visualstudio.com/docs/containers/overview). Usare l'icona Docker a sinistra per aprire la visualizzazione docker. Se si apre l'estensione ora, verrà visualizzata l'esercitazione in esecuzione. Il nome del contenitore ( `angry_taussig` sotto) è un nome creato in modo casuale. Quindi, probabilmente si avrà un nome diverso.

![Contenitore di esercitazione in esecuzione nell'estensione Docker](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Che cos'è un contenitore

Ora che è stato eseguito un contenitore, che cos' *è* un contenitore? In poche parole, un contenitore è semplicemente un altro processo del computer che è stato isolato da tutti gli altri processi nel computer host. Tale isolamento sfrutta gli [spazi dei nomi del kernel e cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), funzionalità che sono state in Linux da molto tempo. Docker ha lavorato per rendere queste funzionalità accessibili e facili da usare.

> [!NOTE]
> **Creazione di contenitori da zero** Se si vuole vedere come vengono creati i contenitori da zero, Liz Rice di Aqua Security ha un video in cui crea un contenitore da zero in go:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Che cos'è un'immagine del contenitore

Quando si esegue un contenitore, viene usato un filesystem isolato. Questo file System personalizzato è fornito da un' **immagine del contenitore**. Poiché l'immagine contiene il file System del contenitore, deve contenere tutti gli elementi necessari per eseguire un'applicazione, ovvero tutte le dipendenze, la configurazione, gli script, i file binari e così via. L'immagine contiene anche altre configurazioni per il contenitore, ad esempio le variabili di ambiente, un comando predefinito da eseguire e altri metadati.

Approfondiremo le immagini in un secondo momento, coprendo argomenti come la sovrapposizione, le procedure consigliate e altro ancora.

> [!NOTE]
> Se si ha familiarità con `chroot` , un contenitore può essere considerato come una versione estesa di `chroot` . Il file System è semplicemente disponibile nell'immagine. Tuttavia, un contenitore aggiunge un isolamento aggiuntivo non disponibile quando si usa semplicemente chroot.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Applicazione](your-application.md)
