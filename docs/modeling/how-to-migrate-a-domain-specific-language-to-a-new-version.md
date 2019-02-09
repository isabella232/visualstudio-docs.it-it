---
title: 'Procedura: Eseguire la migrazione di un linguaggio specifico di dominio a una nuova versione'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbc7694ca7e2b000392aa18dcd45284560ed84ff
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924422"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Procedura: Eseguire la migrazione di un linguaggio specifico di dominio a una nuova versione
È possibile eseguire la migrazione di progetti di definiscono e usano il linguaggio specifico di dominio per [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] dalla versione di [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] che è stato distribuito con [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].

 Uno strumento di migrazione viene fornito come parte di [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. Lo strumento converte i progetti di Visual Studio e le soluzioni che utilizzano o definiscono gli strumenti DSL.

 È necessario eseguire lo strumento di migrazione in modo esplicito: non viene avviato automaticamente quando si apre una soluzione in Visual Studio. Lo strumento e il documento di indicazioni dettagliate è reperibile in questo percorso:

 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Prima che si esegue la migrazione dei progetti DSL
 Lo strumento di migrazione modifica i file di progetto di Visual Studio (**file con estensione csproj**) e i file di soluzione (**sln**).

#### <a name="to-prepare-projects-for-migration"></a>Per preparare i progetti di migrazione.

-   Assicurarsi che il **file con estensione csproj** e **sln** file possono essere scritti. Se sono sotto controllo del codice sorgente, assicurarsi che vengono estratti.

-   Creare una copia di cartelle di cui che si intende eseguire la migrazione.

## <a name="migrating-a-collection-of-projects"></a>La migrazione di una raccolta di progetti

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Eseguire la migrazione di soluzioni e progetti DSL da Visual Studio 2010

1. Avviare lo strumento di migrazione di DSL.

   -   È possibile avviare lo strumento al prompt dei comandi o fare doppio clic sullo strumento in Windows Explorer (o Esplora File). Lo strumento è in questa posizione:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Scegliere una cartella che contiene soluzioni e progetti che si desidera convertire.

   - Immettere il percorso nella casella nella parte superiore dello strumento, oppure fare clic su **esplorare**.

     Lo strumento di migrazione Visualizza un albero di progetti che definiscono o usare linguaggi specifici di dominio. L'albero include tutti i progetti che usa il **Microsoft.VisualStudio.Modeling.Sdk** oppure **TextTemplating** assembly.

3. Esaminare l'albero dei progetti e deselezionare i progetti che non si desidera convertire.

   -   Selezionare un progetto o una soluzione per visualizzare un elenco delle modifiche che lo strumento.

       > [!NOTE]
       >  Le caselle di controllo da visualizzare accanto ai nomi di cartella non hanno alcun effetto. È necessario espandere le cartelle per ispezionare i progetti e soluzioni.

4. Convertire i progetti.

   1.  Fare clic su **convertire**.

        Prima di ogni file di progetto viene convertito, una copia della _project_**csproj** viene salvato come _progetto_**. vs2008.csproj**

        Una copia della ognuno _soluzione_**sln** viene salvato come _soluzione_**. vs2008.sln**

   2.  Esaminare tutte le conversioni non riuscite segnalati.

        Gli errori vengono segnalati nella finestra di testo. Inoltre, la visualizzazione albero mostra un contrassegno rosso in ogni nodo che non è riuscito a convertire. È possibile fare clic sul nodo per ottenere altre informazioni sull'errore.

5. **Trasforma tutti i modelli** nelle soluzioni contenente correttamente convertire i progetti.

   1.  Aprire la soluzione.

   2.  Scegliere il **Trasforma tutti i modelli** pulsante nell'intestazione di Esplora soluzioni.

       > [!NOTE]
       >  È possibile rendere questo passaggio non necessari. Per altre informazioni, vedere [come automatizzare Trasforma tutti i modelli](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

6. Aggiornare il codice personalizzato nei progetti convertiti.

   -   Provare a compilare i progetti ed esaminare gli eventuali errori.

   -   Eseguire il test della finestra di progettazione.


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedere anche

- [Post di blog correlati](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)