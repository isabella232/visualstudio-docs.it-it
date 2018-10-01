---
title: Convalidare il codice con diagrammi livello | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5430d436684be0bbf50004204da8bcd6a18d9bee
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517678"
---
# <a name="validate-code-with-layer-diagrams"></a>Convalidare il codice con diagrammi livello
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [convalidare il codice con diagrammi delle dipendenze](https://docs.microsoft.com/visualstudio/modeling/validate-code-with-layer-diagrams).  
  
Per assicurarsi che il codice non sia in conflitto con la progettazione, è possibile convalidare il codice con diagrammi livello in Visual Studio. In questo modo è possibile effettuare le operazioni seguenti:  
  
-   Trovare conflitti tra le dipendenze nel codice e le dipendenze nel diagramma livello.  
  
-   Trovare le dipendenze sulle quali potrebbero influire le modifiche proposte.  
  
     Ad esempio, è possibile modificare il diagramma livello per mostrare le potenziali modifiche all'architettura e quindi convalidare il codice per vedere le dipendenze interessate.  
  
-   Effettuare il refactoring o la migrazione del codice in una progettazione diversa.  
  
     Trovare codice o dipendenze che richiedono azioni quando si sposta il codice in un'architettura diversa.  
  
 **Requisiti**  
  
-   Visual Studio  
  
-   Visual Studio sul server Team Foundation Build in uso per convalidare il codice automaticamente con Team Foundation Build  
  
-   Una soluzione che contiene un progetto di modellazione con un diagramma livello. Questo diagramma livello deve essere collegato agli artefatti nei progetti Visual C# .NET o Visual Basic .NET da convalidare. Visualizzare [creare i diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 È possibile convalidare manualmente il codice da un diagramma livello aperto in Visual Studio o da un prompt dei comandi. È inoltre possibile convalidare il codice automaticamente quando sono in esecuzione compilazioni locali o Team Foundation Build. Visualizzare [Video di Channel 9: progettazione e convalidare l'architettura utilizzando i diagrammi livello](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
> [!IMPORTANT]
>  Se si desidera eseguire la convalida dei livelli in Team Foundation Build, è inoltre necessario installare la stessa versione di Visual Studio nel server di compilazione.  
  
-   [Se un elemento supporta la convalida](#SupportsValidation)  
  
-   [Includere altri assembly .NET e i progetti per la convalida](#IncludeReferences)  
  
-   [Convalidare il codice manualmente](#ValidateManually)  
  
-   [Convalidare codice automaticamente](#ValidateAuto)  
  
-   [Risolvere i problemi di convalida dei layer](#TroubleshootingValidation)  
  
-   [Comprendere e risolvere gli errori di convalida di livello](#UnderstandingValidationErrors)  
  
##  <a name="SupportsValidation"></a> Se un elemento supporta la convalida  
 È possibile collegare i livelli a siti Web, documenti Office, file di testo normale e file in progetti condivisi tra più app, ma il processo di convalida non li includerà. Gli errori di convalida non verranno visualizzati per i riferimenti a progetti oppure a assembly collegati a livelli separati quando tra tali livelli non è presente alcuna dipendenza. Tali riferimenti non vengono considerati dipendenze a meno che il codice non li usi.  
  
1.  Nel diagramma livello, selezionare uno o più livelli, fare doppio clic la selezione e quindi fare clic su **Visualizza collegamenti**.  
  
2.  Nelle **Esplora livello**, esaminare le **supporta la convalida** colonna. Se il valore è false, l'elemento non supporta la convalida.  
  
##  <a name="IncludeReferences"></a> Includere altri assembly .NET e i progetti per la convalida  
 Quando si trascinano elementi nel diagramma livello, vengono aggiunti automaticamente a riferimenti a progetti o assembly .NET corrispondente di **riferimenti livello** cartella nel progetto di modellazione. Questa cartella contiene i riferimenti agli assembly e ai progetti analizzati durante la convalida. È possibile includere altri assembly e progetti .NET per la convalida senza trascinarli manualmente nel diagramma livello.  
  
1.  Nelle **Esplora soluzioni**, fare clic sul progetto di modellazione o il **riferimenti livello** cartella e quindi fare clic su **Aggiungi riferimento**.  
  
2.  Nel **Aggiungi riferimento** della finestra di dialogo selezionare gli assembly o i progetti e quindi fare clic su **OK**.  
  
##  <a name="ValidateManually"></a> Convalidare il codice manualmente  
 Se si dispone di un diagramma livello aperto collegato agli elementi della soluzione, è possibile eseguire la **Validate** comando di scelta rapida del diagramma. È anche possibile usare il prompt dei comandi per eseguire la **msbuild** con il **ValidateArchitecture** proprietà personalizzata impostata su **True**. Ad esempio, analogamente alle modifiche nel codice, eseguire regolarmente la convalida dei livelli in modo da rilevare tempestivamente conflitti di dipendenza.  
  
#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Per convalidare il codice da un diagramma livello aperto  
  
1.  Pulsante destro del mouse sulla superficie del diagramma e quindi fare clic su **Convalida architettura**.  
  
    > [!NOTE]
    >  Per impostazione predefinita, il **Build Action** nel file del diagramma (con estensione layerdiagram) livello è impostata su **Validate** in modo che il diagramma è incluso nel processo di convalida.  
  
     Il **elenco errori** finestra segnala tutti gli errori che si verificano. Per altre informazioni sugli errori di convalida, vedere [individuare e risolvere errori di convalida dei layer](#UnderstandingValidationErrors).  
  
2.  Per visualizzare l'origine di ogni errore, fare doppio clic su errore nel **elenco errori** finestra.  
  
    > [!NOTE]
    >  In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] potrebbe essere visualizzata una mappa codice anziché l'origine dell'errore. Ciò si verifica quando il codice presenta una dipendenza in un assembly che non è specificata nel diagramma livello o quando al codice manca una dipendenza specificata nel diagramma livello. Esaminare la mappa del codice o il codice per determinare se la dipendenza deve esistere. Per altre informazioni sulle mappe del codice, vedere [mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md).  
  
3.  Per gestire gli errori, vedere [gestire gli errori di convalida](#ManageErrors).  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>Per convalidare il codice al prompt dei comandi  
  
1.  Aprire il prompt dei comandi di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2.  Effettuare una delle seguenti operazioni:  
  
    -   Per convalidare il codice rispetto a un progetto di modellazione specifico nella soluzione, eseguire [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la seguente proprietà personalizzata.  
  
        ```  
        msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
        ```  
  
         - oppure -  
  
         Passare alla cartella contenente il file di progetto di modellazione (con estensione modelproj) e il diagramma livello, quindi eseguire [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la seguente proprietà personalizzata.  
  
        ```  
        msbuild /p:ValidateArchitecture=true   
        ```  
  
    -   Per convalidare il codice rispetto a tutti i progetti di modellazione nella soluzione, eseguire [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la seguente proprietà personalizzata:  
  
        ```  
        msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
        ```  
  
         - oppure -  
  
         Individuare la cartella della soluzione che deve contenere un progetto di modellazione che a sua volta contiene un diagramma livello, quindi eseguire [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la seguente proprietà personalizzata.  
  
        ```  
        msbuild /p:ValidateArchitecture=true  
        ```  
  
     Verranno elencati tutti gli errori che si verificano. Per altre informazioni sulle [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], vedere [MSBuild](../msbuild/msbuild.md) e [attività MSBuild](../msbuild/msbuild-task.md).  
  
 Per altre informazioni sugli errori di convalida, vedere [individuare e risolvere errori di convalida dei layer](#UnderstandingValidationErrors).  
  
###  <a name="ManageErrors"></a> Gestire gli errori di convalida  
 Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è buona norma registrare un elemento di lavoro in [!INCLUDE[esprfound](../includes/esprfound-md.md)].  
  
> [!WARNING]
>  Per creare un elemento di lavoro o aggiungere un collegamento ad esso, è necessario essere già connessi al controllo del codice sorgente TFS. Se si prova ad aprire una connessione in un'istanza diversa del controllo del codice sorgente TFS, Visual Studio chiude automaticamente la soluzione corrente. Prima di provare a creare un elemento di lavoro o ad aggiungervi un collegamento, verificare di essere già connessi all'istanza appropriata del controllo del codice sorgente. Nelle versioni successive di Visual Studio, i comandi di menu non sono disponibili se non si è connessi a un'istanza del controllo del codice sorgente.  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>Per creare un elemento di lavoro per un errore di convalida  
  
-   Nel **elenco errori** finestra, fare doppio clic su errore, scegliere **Crea elemento di lavoro**e quindi scegliere il tipo di elemento di lavoro che si desidera creare.  
  
 Usare queste attività per gestire gli errori di convalida nel **elenco errori** finestra:  
  
|**Per**|**Seguire questi passaggi**|  
|------------|----------------------------|  
|Eliminare gli errori selezionati durante la convalida|Fare doppio clic su uno o più errori selezionati, scegliere **Gestisci errori di convalida**, quindi fare clic su **Elimina errori**.<br /><br /> Gli errori eliminati vengono visualizzati come barrati. Alla successiva convalida, questi errori non saranno visualizzati.<br /><br /> Gli errori eliminati vengono registrati in un file con estensione suppressions per il file del diagramma livello corrispondente.|  
|Interrompere l'eliminazione di errori selezionati|Fare doppio clic su selezionato eliminati gli errori, scegliere **Gestisci errori di convalida**, quindi fare clic su **Interrompi eliminazione errori**.<br /><br /> Alla successiva convalida, gli errori eliminati selezionati verranno visualizzati.|  
|Ripristinare tutti gli errori eliminati nella **elenco errori** finestra|Fare doppio clic in un punto qualsiasi nella **elenco errori** finestra, scegliere **Gestisci errori di convalida**, quindi fare clic su **Mostra tutti gli errori eliminati**.|  
|Tutti gli errori eliminati da nascondere il **elenco errori** finestra|Fare doppio clic in un punto qualsiasi nella **elenco errori** finestra, scegliere **Gestisci errori di convalida**, quindi fare clic su **Nascondi errori eliminati**.|  
  
##  <a name="ValidateAuto"></a> Convalidare codice automaticamente  
 È possibile eseguire la convalida dei livelli ogni volta che si esegue una compilazione. Se il team usa Team Foundation Build, è possibile eseguire la convalida dei livelli nelle archiviazioni gestite, che si possono specificare creando un'attività personalizzata MSBuild, e usare i rapporti di compilazione per raccogliere gli errori di convalida. Per creare compilazioni di archiviazione gestite, vedere [utilizzare un processo di compilazione di archiviazione gestita per convalidare le modifiche](http://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>Per convalidare automaticamente il codice durante una compilazione locale  
  
-   Usare un editor di testo per aprire il file del progetto di modellazione (.modelproj), quindi includere la proprietà seguente:  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \- oppure -  
  
1.  Nelle **Esplora soluzioni**, fare clic sul progetto che contiene il diagramma livello o diagrammi di modellazione e quindi fare clic su **proprietà**.  
  
2.  Nel **delle proprietà** finestra, impostare il progetto di modellazione **Convalida architettura** proprietà **True**.  
  
     Il progetto di modellazione viene incluso nel processo di convalida.  
  
3.  Nelle **Esplora soluzioni**, fare clic sul file del diagramma (con estensione layerdiagram) livello che si desidera utilizzare per la convalida.  
  
4.  Nel **proprietà** finestra, assicurarsi che il diagramma **azione di compilazione** viene impostata su **Validate**.  
  
     Il diagramma livello viene incluso nel processo di convalida.  
  
 Per gestire gli errori nella finestra Elenco errori, vedere [Gestisci errori di convalida](#ManageErrors).  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Per convalidare codice automaticamente durante un'operazione di Team Foundation Build  
  
1.  Nelle **Team Explorer**, fare doppio clic sulla definizione di compilazione e quindi fare clic su **processo**.  
  
2.  Sotto **parametri processo di compilazione**, espandere **compilazione**e digitare il comando seguente nel **argomenti MSBuild** parametro:  
  
     `/p:ValidateArchitecture=true`  
  
 Per altre informazioni sugli errori di convalida, vedere [individuare e risolvere errori di convalida dei layer](#UnderstandingValidationErrors). Per altre informazioni su [!INCLUDE[esprbuild](../includes/esprbuild-md.md)], vedere:  
  
-   [Compilare l'applicazione](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
-   [Utilizzare il modello predefinito per il processo di compilazione](http://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [Modificare una compilazione Legacy basata su upgradetemplate. Xaml](http://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [Personalizzare il modello di processo di compilazione](http://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [Monitorare lo stato di una compilazione in esecuzione](http://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="TroubleshootingValidation"></a> Risolvere i problemi di convalida dei layer  
 Nella tabella seguente vengono descritti i problemi di convalida dei livelli e la relativa risoluzione. Questi problemi differiscono dagli errori risultanti da conflitti tra il codice e la progettazione. Per altre informazioni su questi errori, vedere [individuare e risolvere errori di convalida dei layer](#UnderstandingValidationErrors).  
  
|**Problema**|**Causa possibile**|**Risoluzione**|  
|---------------|------------------------|--------------------|  
|Gli errori di convalida non si verificano come previsto.|La convalida non funziona sui diagrammi livello copiati da altri diagrammi livello in Esplora soluzioni e appartenenti allo stesso progetto di modellazione. I diagrammi livello copiati in questo modo contengono gli stessi riferimenti del diagramma livello originale.|Aggiungere un nuovo diagramma livello al progetto di modellazione.<br /><br /> Copiare gli elementi dal diagramma livello di origine al nuovo diagramma.|  
  
##  <a name="UnderstandingValidationErrors"></a> La comprensione e la risoluzione di errori a livello di convalida  
 Quando si esegue la convalida di codice in base a un diagramma livello, se il codice è in conflitto con la progettazione si verificano errori di convalida. In presenza delle condizioni seguenti è possibile ad esempio che si verifichino errori di convalida:  
  
-   Un elemento viene assegnato al livello errato. In questo caso, spostare l'elemento.  
  
-   Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.  
  
 Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. È possibile eseguire questa attività in modo iterativo.  
  
 Nella sezione seguente viene descritta la sintassi usata negli errori, viene illustrato il significato degli errori e vengono indicate le operazioni che è possibile eseguire per risolverli o gestirli.  
  
|**Sintassi**|**Descrizione**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*Elementon* è un elemento che è associato a un livello nel diagramma livello.<br /><br /> *Tipoelementon* è il tipo di *Elementon*, ad esempio un **classe** oppure **metodo**, ad esempio:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metodo)|  
|*NamespaceNameN*|Nome di uno spazio dei nomi.|  
|*LayerNameN*|Nome di un livello nel diagramma livello.|  
|*Tipodipendenza*|Il tipo di relazione di dipendenza tra *Elemento1* e *elemento2*. Ad esempio, *Elemento1* ha una **chiamate** relazione con *elemento2*.|  
  
|**Sintassi errore**|**Descrizione dell'errore**|  
|----------------------|---------------------------|  
|AV0001: Dipendenza non valida: *Elemento1*(*Tipoartefatto1*)--> *elemento2*(*Tipoartefatto2*)<br /><br /> Livelli: *Nomelivello1*, *Nomelivello2* &#124; dipendenze: *Tipodipendenza*|*Elemento1* nelle *Nomelivello1* non deve avere una dipendenza *elemento2* in *Nomelivello2* perché *Nomelivello1* non ha una dipendenza diretta *Nomelivello2*.|  
|AV1001: Namespace non è valido: *artefatto*<br /><br /> Livello: *nomelivello* &#124; obbligatorio Namespace: *Nomespaziodeinomi1* &#124; corrente Namespace: *Nomespaziodeinomi2*|*Nomelivello* richiede che gli elementi collegati appartengano a *Nomespaziodeinomi1*. *Artefatto* le novità *Nomespaziodeinomi2*, non *Nomespaziodeinomi1*.|  
|AV1002: Dipende Namespace non consentito: *Elemento1*(*Tipoartefatto1*) &#124; *elemento2*(*Tipoartefatto2*)<br /><br /> Livello: *nomelivello* &#124; non è consentito Namespace: *NomeSpazioDeiNomi* &#124; dipendenze: *Tipodipendenza*|*Nomelivello* richiede che gli elementi associati non dipendano *NomeSpazioDeiNomi*. *Elemento1* non può dipendere *elemento2* perché *elemento2* in *NomeSpazioDeiNomi*.|  
|AV1003: Nello Namespace non consentito: *artefatto*(*ArtifactType*)<br /><br /> Livello: *nomelivello* &#124; non è consentito Namespace: *NomeSpazioDeiNomi*|*Nomelivello* richiede che gli elementi collegati non appartengano allo *NomeSpazioDeiNomi*. *Artefatto* a cui appartiene *NomeSpazioDeiNomi*.|  
|AV3001: collegamento mancante: livello '*nomelivello*'Collega a'*artefatto*' che non viene trovato. Probabilmente manca un riferimento a un assembly.|*Nomelivello* Collega a un elemento che non è stato trovato. Ad esempio, è possibile che manchi un collegamento a una classe perché nel progetto di modellazione manca un riferimento all'assembly che contiene la classe.|  
|AV9001: errori interni durante l'analisi dell'architettura. I risultati potrebbero non essere completi. Per altre informazioni, vedere il log dettagliato degli eventi di compilazione o la finestra di output.|Per altre informazioni, vedere il log degli eventi di compilazione o la finestra di output.|  
  
## <a name="security"></a>Sicurezza  
  
## <a name="see-also"></a>Vedere anche  
 [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)



