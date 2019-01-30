---
title: Creare un'installazione offline
description: Informazioni su come installare Visual Studio offline quando la connessione Internet non è affidabile o la larghezza di banda è ridotta.
ms.date: 01/15/2019
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbf0f68f090219aea8f3ddde31e697463f8e9ee3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035523"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Creare un'installazione offline di Visual Studio 2017

Visual Studio 2017 è stato progettato per funzionare correttamente in un'ampia gamma di configurazioni di computer e reti. Sebbene sia consigliabile provare il [programma di installazione Web di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), che è un file di piccole dimensioni e consente di rimanere aggiornati con tutte le correzioni e funzionalità più recenti, è comprensibile che non tutti gli utenti abbiano questa possibilità.

Ad esempio, la connessione Internet potrebbe essere inaffidabile o la larghezza di banda disponibile limitata. In questi casi, è possibile usare la nuova funzionalità "Scarica tutto, quindi installa" per scaricare i file prima di installarli oppure è possibile usare la riga di comando per creare una cache locale dei file.

> [!NOTE]
> Gli amministratori dell'organizzazione che vogliono distribuire Visual Studio 2017 in una rete di workstation client protette da Internet tramite firewall possono vedere le pagine [Creare un'installazione di rete di Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) e [Installare i certificati necessari per l'installazione offline di Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="use-the-download-all-then-install-feature"></a>Usare la funzionalità "Scarica tutto, quindi installa"

[**Novità della versione 15.8**](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017#install
): dopo aver scaricato il programma di installazione Web, selezionare la nuova opzione **Scarica tutto, quindi installa** nel programma di installazione di Visual Studio. Continuare quindi con l'installazione.

   ![Opzione "Scarica tutto, quindi installa"](media/download-all-then-install.png)

## <a name="use-the-command-line-to-create-a-local-cache"></a>Usare la riga di comando per creare una cache locale

Dopo aver scaricato un piccolo programma di avvio automatico, usare la riga di comando per creare una cache locale. Usare quindi la cache locale per installare Visual Studio. Questo processo sostituisce i file ISO disponibili per le versioni precedenti.

Ecco come fare.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Passaggio 1: Scaricare il programma di avvio automatico di Visual Studio

Per completare questo passaggio è necessario avere una connessione Internet.

Iniziare scaricando il programma di bootstrap relativo all'edizione di Visual Studio selezionata. Il file di installazione, o programma di avvio automatico, sarà uguale o simile a uno dei seguenti.

| Edizione                    | File                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Community di Visual Studio    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

### <a name="step-2---create-a-local-install-cache"></a>Passaggio 2: Creare una cache di installazione locale

Per completare questo passaggio è necessario avere una connessione Internet.

> [!IMPORTANT]
> Se si installa Visual Studio Community 2017, è necessario attivarlo entro 30 giorni dall'installazione. È necessaria una connessione Internet.

Aprire un prompt dei comandi e usare uno dei comandi presenti negli esempi seguenti. Negli esempi qui elencati si presuppone che si stia usando Visual Studio Community Edition: modificare il comando in base all'edizione in uso.

> [!TIP]
> Per evitare un errore, assicurarsi che il percorso di installazione completo sia composto da meno di 80 caratteri.

- Per lo sviluppo per Web .NET e desktop .NET, eseguire:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- Per lo sviluppo per desktop .NET e Office, eseguire:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Per lo sviluppo per desktop C++, eseguire:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Per creare un layout locale completo con tutte le funzionalità (dato l'_elevato_ numero di funzionalità, questa operazione richiederà molto&mdash; tempo), eseguire:

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

  > [!NOTE]
  > Un layout di Visual Studio 2017 completo richiede almeno 35 GB di spazio su disco. Vedere [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) per informazioni su come creare un layout con i soli componenti da installare.

Se si vuole installare una lingua diversa dall'inglese, sostituire `en-US` con impostazioni locali diverse dall'[Elenco delle impostazioni locali delle lingue](#list-of-language-locales). Usare quindi l'[elenco di componenti e carichi di lavoro disponibili](workload-and-component-ids.md) per personalizzare ulteriormente la cache di installazione.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Passaggio 3: Installare Visual Studio dalla cache locale

> [!TIP]
> Quando si esegue l'installazione da una cache locale, vengono usate le versioni locali di ogni file. Se, tuttavia, durante l'installazione si selezionano componenti non contenuti nella cache, il programma di installazione tenterà di scaricarli da Internet.

Per assicurarsi che vengano installati solo i file scaricati in precedenza, usare le stesse opzioni della riga di comando usate per creare la cache di layout. Ad esempio, se è stata creata una cache di layout con il comando seguente:

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Usare quindi questo comando per eseguire l'installazione:

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

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
| zh-CN | Cinese semplificato |
| zh-TW | Cinese tradizionale |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

- [Creare un'installazione di rete di Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md)
- [Installare i certificati necessari per l'installazione offline di Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md)
