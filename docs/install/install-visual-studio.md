---
title: Installare Visual Studio
titleSuffix: ''
description: Informazioni dettagliate sull'installazione di Visual Studio.
ms.date: 05/07/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4ab9fb30a1268778f47a0190d1b16b1cd48d974
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958436"
---
# <a name="install-visual-studio-2017"></a>Installare Visual Studio 2017

In questo articolo viene presentato un nuovo modo per installare Visual Studio! Nella versione più recente è stata semplificata la procedura che consente di selezionare e installare solo le funzionalità necessarie. È anche stato ridotto il footprint minimo di Visual Studio in modo che possa essere installato più rapidamente, limitando l'impatto sul sistema.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Installare Visual Studio per Mac](/visualstudio/mac/installation).

Per altre informazioni sulle novità in questa versione, vedere le [note sulla versione](/visualstudio/releasenotes/vs2017-relnotes) Microsoft.

Tutto pronto? Sarà illustrata una procedura dettagliata.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Passaggio 1: Verificare che il computer sia pronto per Visual Studio

Prima di iniziare l'installazione di Visual Studio:

1. Controllare i [requisiti di sistema](/visualstudio/productinfo/vs2017-system-requirements-vs) I requisiti consentono di verificare se il computer supporta Visual Studio 2017.
2. Applicare gli aggiornamenti più recenti di Windows. Tali aggiornamenti consentono di avere la certezza che nel computer siano presenti sia gli aggiornamenti di sicurezza più recenti sia i componenti di sistema necessari per Visual Studio.
3. Riavviare il computer. Il riavvio evita che eventuali installazioni o aggiornamenti in sospeso impediscano l'installazione di Visual Studio.
4. Liberare spazio. Rimuovere le applicazioni e i file non necessari da %SystemDrive% eseguendo, ad esempio, l'app Pulitura disco.

Per domande sull'esecuzione di Visual Studio 2017 side by side con versioni precedenti di Visual Studio, vedere [Compatibilità con le versioni precedenti](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Passaggio 2: Scaricare Visual Studio

Scaricare quindi il file del programma di avvio automatico di Visual Studio. A tale scopo, fare clic sul pulsante seguente, selezionare l'edizione di Visual Studio 2017 desiderata, fare clic su **Salva** e quindi fare clic su **Apri cartella**.

 > [!div class="button"]
 > [Scarica Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

|         |         |
|---------|---------|
|  ![icona della telecamera](media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) su come scaricare il file del programma di avvio automatico di Visual Studio e selezionare l'edizione di Visual Studio adatta alle proprie esigenze. |

## <a name="step-3---install-the-visual-studio-installer"></a>Passaggio 3: Installare il programma di installazione di Visual Studio

Eseguire quindi il file del programma di avvio automatico per installare il programma di installazione di Visual Studio. Questo nuovo programma di installazione semplificato include tutto ciò che occorre per installare e personalizzare Visual Studio 2017.

1. Dalla cartella **Download** fare doppio clic sul file del programma di avvio automatico corrispondente o simile a uno dei file seguenti:

   * **vs_enterprise.exe** per Visual Studio Enterprise
   * **vs_professional.exe** per Visual Studio Professional
   * **vs_community.exe** per Visual Studio Community  <br><br>

   Se si riceve una comunicazione di Controllo dell'account utente, fare clic su **Sì**.

2. Verrà richiesto di confermare le [Condizioni di licenza](https://visualstudio.microsoft.com/license-terms/) e l'[Informativa sulla privacy](https://privacy.microsoft.com/privacystatement) di Microsoft. Scegliere **Continua**.

   ![Condizioni di licenza e informativa sulla privacy](media/vs2017-privacy-and-license-terms.PNG "Condizioni di licenza e informativa sulla privacy")

## <a name="step-4---select-workloads"></a>Passaggio 4: Selezionare i carichi di lavoro

Dopo aver installato il programma di installazione, è possibile usarlo per personalizzare l'installazione selezionando i set di funzionalità o carichi di lavoro desiderati. Ecco come fare.

1. Individuare il carico di lavoro che si vuole installare nella schermata d'**installazione di Visual Studio**.

   ![Selezionare un carico di lavoro dalla finestra di dialogo della configurazione di Visual Studio 2017](../install/media/install-visual-studio-community.png)

     Scegliere ad esempio il carico di lavoro "Sviluppo per desktop .NET". Include l'editor principale predefinito che offre supporto di base per la modifica del codice per oltre 20 linguaggi, la possibilità di aprire e modificare il codice da qualsiasi cartella senza che sia necessario un progetto e il controllo del codice sorgente integrato.

2. Dopo aver selezionato il carico di lavoro, fare clic su **Installa**.

    A questo punto si apriranno diverse schermate di stato in cui sarà visualizzato l'avanzamento dell'installazione di Visual Studio.

3. Dopo aver installato i carichi di lavoro e i componenti nuovi, fare clic su **Avvia**.

> [!TIP]
> In qualsiasi momento dopo l'installazione, è possibile installare i carichi di lavoro o i componenti che non sono stati installati inizialmente. Se si ha Visual Studio aperto, passare a **Strumenti** > **Ottieni strumenti e funzionalità** che apre il programma di installazione di Visual Studio. In alternativa, aprire **il programma di installazione di Visual Studio** dal menu Start. Da qui, è possibile selezionare i carichi di lavoro o i componenti che si vogliono installare e fare clic su **Modifica**.

|         |         |
|---------|---------|
|  ![icona della telecamera](media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) su come installare il programma di installazione di Visual Studio e quindi installare un carico di lavoro. |

## <a name="step-5---select-individual-components-optional"></a>Passaggio 5: Selezionare singoli componenti (facoltativo)

Se non si vuole usare la funzionalità Carichi di lavoro per personalizzare l'installazione di Visual Studio, è possibile scegliere di installare singoli componenti. Per selezionare componenti singoli, fare clic sull'opzione **Singoli componenti** nel programma di installazione di Visual Studio, selezionare i componenti da installare e seguire le istruzioni.

  ![Visual Studio 2017 - Installare singoli componenti](media/vs2017-components.PNG "Installare singoli componenti di Visual Studio")

  |         |         |
  |---------|---------|
  |  ![icona della telecamera](media/video-icon.png "Guardare un video")  |   [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) su come installare un singolo componente usando il programma di installazione di Visual Studio. |

## <a name="step-6---install-language-packs-optional"></a>Passaggio 6: Installare i Language Pack (facoltativo)

Per impostazione predefinita, alla prima esecuzione il programma di installazione tenta di trovare una corrispondenza con la lingua del sistema operativo. Per installare Visual Studio 2017 nella lingua prescelta, fare clic sull'opzione **Language Pack** dal programma di installazione di Visual Studio e seguire le istruzioni visualizzate.

  ![Visual Studio 2017 - Installare Language Pack](media/vs2017-languages.PNG "Installare Language Pack di Visual Studio")

  |         |         |
  |---------|---------|
  |  ![icona della telecamera](media/video-icon.png "Guardare un video")  |   [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) su come installare un Language Pack usando il programma di installazione di Visual Studio. |

### <a name="change-the-installer-language-from-the-command-line"></a>Modificare la lingua del programma di installazione dalla riga di comando

Un altro modo per poter modificare la lingua predefinita consiste nell'eseguire il programma di installazione dalla riga di comando. Ad esempio, usare il comando seguente per forzare l'esecuzione in inglese del programma di installazione: `vs_installer.exe --locale en-US`. Il programma di installazione memorizza questa impostazione per l'esecuzione successiva. Il programma di installazione supporta i token delle lingue seguenti: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru e tr-tr.

## <a name="step-7---change-the-installation-location-optional"></a>Passaggio 7: Cambiare il percorso di installazione (facoltativo)

**Novità della versione 15.7**: è ora possibile ridurre lo spazio occupato dall'installazione di Visual Studio nell'unità di sistema. È possibile scegliere di spostare la Download Cache, i componenti condivisi, gli SDK e gli strumenti in unità diverse e mantenere Visual Studio nell'unità che lo esegue più rapidamente.

  ![Visual Studio 2017 - Cambiare il percorso di installazione](media/installation-options-by-location.png "Cambiare il percorso di installazione")

Per altre informazioni, vedere la pagina [Cambiare i percorsi di installazione in Visual Studio](change-installation-locations.md).

## <a name="step-8---start-developing"></a>Passaggio 8: Avviare lo sviluppo

1. Al termine dell'installazione di Visual Studio, fare clic sul pulsante **Avvia** per iniziare a sviluppare con Visual Studio.

2. Fare clic su **File** e quindi su **Nuovo progetto**.

3. Selezionare un tipo di progetto.

   Ad esempio, per [compilare un'app C++](../ide/getting-started-with-cpp-in-visual-studio.md), fare clic su **Installati**, espandere **Visual C++** e selezionare il tipo di progetto C++ che si vuole compilare.

   Per [compilare un'app C#](../get-started/csharp/tutorial-wpf.md), fare clic su **Installati**, espandere **Visual C#** e selezionare il tipo di progetto C# che si vuole compilare.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Aggiornare Visual Studio 2017](update-visual-studio.md)
* [Modificare Visual Studio 2017](modify-visual-studio.md)
* [Disinstallare Visual Studio 2017](uninstall-visual-studio.md)
* [Creare un'installazione offline di Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Installare Visual Studio per Mac](/visualstudio/mac/installation)