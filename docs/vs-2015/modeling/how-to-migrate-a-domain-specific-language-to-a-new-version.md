---
title: 'Procedura: eseguire la migrazione di un Domain-Specific Language a una nuova versione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45f7b38f7dbb6ea470b2d9e186dc8e6bf4b33b1e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657333"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Procedura: eseguire la migrazione di un linguaggio specifico di dominio a una nuova versione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile eseguire la migrazione di progetti che definiscono e utilizzano il linguaggio specifico di dominio per [!INCLUDE[vs2010](../includes/vs2010-md.md)] dalla versione di [!INCLUDE[dsl](../includes/dsl-md.md)] distribuita con [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 Uno strumento di migrazione viene fornito come parte di [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)]. Lo strumento converte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] progetti e soluzioni che utilizzano o definiscono gli strumenti DSL.

 È necessario eseguire lo strumento di migrazione in modo esplicito: non viene avviato automaticamente quando si apre una soluzione in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Lo strumento e il documento dettagliato delle linee guida sono disponibili in questo percorso:

 **%Programmi%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Prima di eseguire la migrazione dei progetti DSL
 Lo strumento di migrazione modifica [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] file di progetto (con**estensione csproj**) e i file di soluzione (con**estensione sln**).

#### <a name="to-prepare-projects-for-migration"></a>Per preparare i progetti per la migrazione.

- Verificare che i file con **estensione csproj** e **sln** possano essere scritti. Se sono sottoposti al controllo del codice sorgente, assicurarsi che siano estratti.

- Creare una copia delle cartelle di cui si intende eseguire la migrazione.

## <a name="migrating-a-collection-of-projects"></a>Migrazione di una raccolta di progetti

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Per eseguire la migrazione di progetti e soluzioni DSL a Visual Studio 2010

1. Avviare lo strumento di migrazione DSL.

   - È possibile fare doppio clic sullo strumento in Esplora risorse (o Esplora file) oppure avviare lo strumento da un prompt dei comandi. Lo strumento si trova in questa posizione:

        **%Programmi%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Scegliere una cartella che contiene le soluzioni e i progetti che si desidera convertire.

   - Immettere il percorso nella casella nella parte superiore dello strumento oppure fare clic su **Sfoglia**.

     Tramite lo strumento di migrazione viene visualizzato un albero di progetti che definiscono o utilizzano DSLs. L'albero include tutti i progetti che usano gli assembly **Microsoft. VisualStudio. Modeling. SDK** o **TextTemplating** .

3. Esaminare l'albero dei progetti e deselezionare i progetti che non si desidera convertire.

   - Selezionare un progetto o una soluzione per visualizzare un elenco delle modifiche che lo strumento farà.

       > [!NOTE]
       > Le caselle di controllo visualizzate accanto ai nomi di cartella non hanno alcun effetto. È necessario espandere le cartelle per esaminare i progetti e le soluzioni.

4. Convertire i progetti.

   1. Fare clic su **Converti**.

        Prima di convertire ogni file di progetto, una copia di _Project_ **. csproj** viene salvata come _Project_ **. VS2008. csproj**

        Una copia di ogni _Solution_ **. sln** viene salvata come _Solution_ **. VS2008. sln**

   2. Esaminare le conversioni non riuscite segnalate.

        Gli errori vengono segnalati nella finestra di testo. Inoltre, la visualizzazione albero Mostra un flag rosso in ogni nodo che non è stato possibile convertire. Per ottenere ulteriori informazioni su tale errore, è possibile fare clic sul nodo.

5. **Trasforma tutti i modelli** in soluzioni che contengono progetti convertiti correttamente.

   1. Aprire la soluzione.

   2. Fare clic sul pulsante **trasforma tutti i modelli** nell'intestazione del Esplora soluzioni.

       > [!NOTE]
       > È possibile fare in modo che questo passaggio non sia necessario. Per ulteriori informazioni, vedere [come automatizzare Transform All Templates](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

6. Aggiornare il codice personalizzato nei progetti convertiti.

   - Tentare di compilare i progetti ed esaminare eventuali errori.

   - Testare la finestra di progettazione.

## <a name="see-also"></a>Vedere anche
 [Novità relative all'SDK di visualizzazione e modellazione](../misc/what-s-new-in-visualization-and-modeling-sdk.md)
