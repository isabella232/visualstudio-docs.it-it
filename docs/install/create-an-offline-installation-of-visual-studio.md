---
title: Creare un'installazione offline
description: Informazioni su come installare Visual Studio offline quando la connessione Internet non è affidabile o la larghezza di banda è ridotta.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2e4a7e0f9335971bb026ccc1c6b977680d9e3121
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949558"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Creare un'installazione offline di Visual Studio

::: moniker range="vs-2017"

Visual Studio 2017 è stato progettato per funzionare correttamente in un'ampia gamma di configurazioni di computer e reti. Sebbene sia consigliabile provare il programma di [installazione Web di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads) &mdash; , un file di dimensioni ridotte, che consente di rimanere aggiornati con tutte le correzioni e le funzionalità più recenti, &mdash; è possibile che non sia possibile.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 è stato progettato per funzionare correttamente in un'ampia gamma di configurazioni di computer e reti. Sebbene sia consigliabile provare il programma di [installazione Web di Visual Studio](https://visualstudio.microsoft.com/downloads) &mdash; , un file di dimensioni ridotte, che consente di rimanere aggiornati con tutte le correzioni e le funzionalità più recenti, &mdash; è possibile che non sia possibile.

::: moniker-end

Ad esempio, la connessione Internet potrebbe essere inaffidabile o la larghezza di banda disponibile limitata. In questi casi è possibile usare la nuova funzionalità "Scarica tutto, quindi installa" per scaricare i file prima di installare oppure è possibile usare la riga di comando per creare una cache locale dei file.

> [!NOTE]
> Gli amministratori dell'organizzazione che vogliono distribuire Visual Studio in una rete di workstation client protette da Internet tramite firewall possono vedere le pagine [Creare un'installazione di rete di Visual Studio](../install/create-a-network-installation-of-visual-studio.md) e [Installare i certificati necessari per l'installazione offline di Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="use-the-download-all-then-install-feature"></a>Usare la funzionalità "Scarica tutto, quindi installa"

::: moniker range="vs-2017"

[**Novità della versione 15,8**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): dopo il download del programma di installazione Web, selezionare la nuova opzione **Scarica tutto, quindi installa** dal programma di installazione di Visual Studio. Continuare quindi con l'installazione.

   ![Opzione "Scarica tutto, quindi installa"](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

dopo aver scaricato il programma di installazione Web, selezionare la nuova opzione **Scarica tutto, quindi installa** nel programma di installazione di Visual Studio. Continuare quindi con l'installazione.

   ![Opzione "Scarica tutto, quindi installa"](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

La funzionalità "Scarica tutto, quindi installa" è stata progettata in modo da poter scaricare Visual Studio come una singola installazione per lo stesso computer in cui è stato scaricato. In questo modo, è possibile disconnettersi in modo sicuro dal Web prima di installare Visual Studio.

> [!IMPORTANT]
> Non usare la funzionalità "Scarica tutto, quindi installa" per creare una cache offline da trasferire in un altro computer. Non è progettata per funzionare in questo modo. <br><br>Se si vuole creare una cache offline per installare Visual Studio in un altro computer, vedere la sezione [Usare la riga di comando per creare una cache locale](#use-the-command-line-to-create-a-local-cache) di questa pagina per informazioni su come creare una cache locale oppure la pagina [Creare un'installazione di rete di Visual Studio](../install/create-a-network-installation-of-visual-studio.md) per informazioni su come creare una cache di rete.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Usare la riga di comando per creare una cache locale

Dopo aver scaricato un piccolo programma di avvio automatico, usare la riga di comando per creare una cache locale. Usare quindi la cache locale per installare Visual Studio. Questo processo sostituisce i file ISO disponibili per le versioni precedenti.

Ecco come.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Passaggio 1: Scaricare il programma di avvio automatico di Visual Studio

Per completare questo passaggio è necessaria una connessione Internet.

::: moniker range="vs-2017"

Per ottenere un programma di avvio automatico per Visual Studio 2017, vedere la pagina di download di [versioni precedenti di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) per informazioni dettagliate su come eseguire questa operazione.

Il file eseguibile di installazione &mdash; o, per essere più specifici, il file del programma di avvio automatico &mdash; deve corrispondere o essere simile a uno dei seguenti.

| Edizione | Nome file |
|-------------|-----------------------|
|Community di Visual Studio | vs_community.exe |
|Visual Studio Professional | vs_professional.exe |
|Visual Studio Enterprise | vs_enterprise.exe |
|Visual Studio Build Tools   | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

Iniziare scaricando il programma di bootstrap relativo all'edizione di Visual Studio selezionata. Il file di installazione, o programma di avvio automatico, sarà uguale o simile a uno dei seguenti.

| Edizione                    | File                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Community di Visual Studio    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

>[!TIP]
>Se in precedenza è stato scaricato un file del programma di avvio automatico e si vuole verificarne la versione, ecco come. In Windows aprire Esplora file, fare clic con il pulsante destro del mouse sul file del programma di avvio automatico, scegliere **Proprietà**, scegliere la scheda **Dettagli** , quindi visualizzare il numero di **versione del prodotto** . Per abbinare tale numero a una versione di Visual Studio, vedere la pagina relativa ai [numeri di build e alle date di rilascio di Visual Studio](visual-studio-build-numbers-and-release-dates.md) .

### <a name="step-2---create-a-local-install-cache"></a>Passaggio 2: Creare una cache di installazione locale

Per completare questo passaggio è necessaria una connessione Internet.

> [!IMPORTANT]
> Se si installa Visual Studio Community, è necessario attivarlo entro 30 giorni dall'installazione. È necessaria una connessione Internet.

Aprire un prompt dei comandi e usare uno dei comandi presenti negli esempi seguenti. Negli esempi qui elencati si presuppone che si stia usando Visual Studio Community Edition: modificare il comando in base all'edizione in uso.

> [!TIP]
> Per evitare un errore, assicurarsi che il percorso di installazione completo sia composto da meno di 80 caratteri.

- Per lo sviluppo per Web .NET e desktop .NET, eseguire:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- Per lo sviluppo per desktop .NET e Office, eseguire:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Per lo sviluppo per desktop C++, eseguire:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Per creare un layout locale completo con tutte le funzionalità (questa operazione richiede molto tempo &mdash; sono disponibili _molte_ funzionalità), eseguire:

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Un layout di Visual Studio completo richiede almeno 35 GB di spazio su disco. Per ulteriori informazioni, vedere [requisiti di sistema](/visualstudio/productinfo/vs2017-system-requirements-vs/). Per informazioni su come creare un layout solo con i componenti che si desidera installare, vedere [Usare parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Un layout di Visual Studio completo richiede almeno 35 GB di spazio su disco. Per ulteriori informazioni, vedere [requisiti di sistema](/visualstudio/releases/2019/system-requirements/). Per informazioni su come creare un layout solo con i componenti che si desidera installare, vedere [Usare parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

Se si vuole installare una lingua diversa dall'inglese, sostituire `en-US` con impostazioni locali diverse dall'[Elenco delle impostazioni locali delle lingue](#list-of-language-locales). Usare quindi l'[elenco di componenti e carichi di lavoro disponibili](workload-and-component-ids.md) per personalizzare ulteriormente la cache di installazione.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Passaggio 3: Installare Visual Studio dalla cache locale

> [!TIP]
> Quando si esegue l'installazione da una cache locale, vengono usate le versioni locali di ogni file. Se, tuttavia, durante l'installazione si selezionano componenti non contenuti nella cache, il programma di installazione tenterà di scaricarli da Internet.

::: moniker range="vs-2019"
> [!IMPORTANT]
> Per le installazioni offline, se viene visualizzato un messaggio di errore che indica che non è possibile trovare un prodotto corrispondente ai parametri seguenti, assicurarsi di usare l' `--noweb` opzione con la versione 16.3.5 o successiva.
>
::: moniker-end

Per assicurarsi che vengano installati solo i file scaricati in precedenza, usare le stesse opzioni della riga di comando usate per creare la cache di layout. Ad esempio, se è stata creata una cache di layout con il comando seguente:

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Usare quindi questo comando per eseguire l'installazione:

```cmd
c:\vslayout\vs_community.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

Per altri esempi su come usare i [parametri della riga di comando](use-command-line-parameters-to-install-visual-studio.md), vedere la pagina [esempi di parametri della riga di comando per l'installazione di Visual Studio](command-line-parameter-examples.md) . 

> [!NOTE]
> Se viene generato un errore che indica che una firma non è valida, è necessario installare i certificati aggiornati. Aprire la cartella dei certificati presente nella cache offline. Fare doppio clic su ognuno dei file di certificato e quindi seguire la procedura guidata di gestione dei certificati. Se viene richiesta una password, lasciare il campo vuoto.

### <a name="list-of-language-locales"></a>Elenco delle impostazioni locali delle lingue

| **Impostazioni locali** | **Lingua** |
| ----------------------- | --------------- |
| cs-CZ | Ceco |
| de-DE | Tedesco |
| en-US | Inglese |
| es-ES | Spagnolo |
| fr-FR | Francese |
| it-IT | Italiano |
| ja-JP | Giapponese |
| ko-KR | Coreano |
| pl-PL | Polacco |
| pt-BR | Portoghese (Brasile) |
| ru-RU | Russo |
| tr-TR | Turco |
| zh-CN | Cinese (semplificato) |
| zh-TW | Cinese (tradizionale) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

- [Creare un'installazione di rete di Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Installare i certificati necessari per l'installazione offline di Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
