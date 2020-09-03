---
title: 'Procedura: eseguire la migrazione di un linguaggio specifico di dominio a una nuova versione'
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8bdaea1267d0bf69078aec5739291e72db8dfda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532611"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Procedura: eseguire la migrazione di un linguaggio specifico di dominio a una nuova versione
È possibile eseguire la migrazione di progetti che definiscono e utilizzano il linguaggio specifico di dominio a [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] dalla versione di [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] distribuita con [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] .

 Viene fornito uno strumento di migrazione come parte di [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] . Lo strumento converte i progetti e le soluzioni di Visual Studio che usano o definiscono gli strumenti DSL.

 È necessario eseguire lo strumento di migrazione in modo esplicito: non viene avviato automaticamente quando si apre una soluzione in Visual Studio. Lo strumento e il documento dettagliato delle linee guida sono disponibili in questo percorso:

 **%Programmi%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Prima di eseguire la migrazione dei progetti DSL
 Lo strumento di migrazione modifica i file di progetto di Visual Studio (con**estensione csproj**) e i file di soluzione (con**estensione sln**).

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

        Prima di convertire ogni file di progetto, una copia di _Project_**. csproj** viene salvata come _Project_**. VS2008. csproj**

        Una copia di ogni _Solution_**. sln** viene salvata come _Solution_**. VS2008. sln**

   2. Esaminare le conversioni non riuscite segnalate.

        Gli errori vengono segnalati nella finestra di testo. Inoltre, la visualizzazione albero Mostra un flag rosso in ogni nodo che non è stato possibile convertire. Per ottenere ulteriori informazioni su tale errore, è possibile fare clic sul nodo.

5. **Trasforma tutti i modelli** in soluzioni che contengono progetti convertiti correttamente.

   1. Aprire la soluzione.

   2. Fare clic sul pulsante **trasforma tutti i modelli** nell'intestazione del Esplora soluzioni.

       > [!NOTE]
       > È possibile fare in modo che questo passaggio non sia necessario. Per ulteriori informazioni, vedere [come automatizzare Transform All Templates](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

6. Aggiornare il codice personalizzato nei progetti convertiti.

   - Tentare di compilare i progetti ed esaminare eventuali errori.

   - Testare la finestra di progettazione.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedere anche

- [Post di blog correlati](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)