---
title: Convalidare il codice con diagrammi livello | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45b82ece15cfef4d313764027c0220453a6d4849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845433"
---
# <a name="validate-code-with-layer-diagrams"></a>Convalidare il codice con diagrammi livello
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per assicurarsi che il codice non sia in conflitto con la progettazione, è possibile convalidare il codice con diagrammi livello in Visual Studio. In questo modo è possibile effettuare le operazioni seguenti:

- Trovare conflitti tra le dipendenze nel codice e le dipendenze nel diagramma livello.

- Trovare le dipendenze sulle quali potrebbero influire le modifiche proposte.

   Ad esempio, è possibile modificare il diagramma livello per mostrare le potenziali modifiche all'architettura e quindi convalidare il codice per vedere le dipendenze interessate.

- Effettuare il refactoring o la migrazione del codice in una progettazione diversa.

   Trovare codice o dipendenze che richiedono azioni quando si sposta il codice in un'architettura diversa.

  **Requisiti**

- Visual Studio

- Visual Studio sul server Team Foundation Build in uso per convalidare il codice automaticamente con Team Foundation Build

- Una soluzione che contiene un progetto di modellazione con un diagramma livello. Questo diagramma livello deve essere collegato agli artefatti nei progetti Visual C# .NET o Visual Basic .NET da convalidare. Vedere [creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md).

  Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

  È possibile convalidare manualmente il codice da un diagramma livello aperto in Visual Studio o da un prompt dei comandi. È inoltre possibile convalidare il codice automaticamente quando sono in esecuzione compilazioni locali o Team Foundation Build. Vedere [video di Channel 9: progettare e convalidare l'architettura usando i diagrammi livello](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Se si desidera eseguire la convalida dei livelli in Team Foundation Build, è inoltre necessario installare la stessa versione di Visual Studio nel server di compilazione.

- [Vedere se un elemento supporta la convalida](#SupportsValidation)

- [Includere altri progetti e assembly .NET per la convalida](#IncludeReferences)

- [Convalidare manualmente il codice](#ValidateManually)

- [Convalidare automaticamente il codice](#ValidateAuto)

- [Risolvere i problemi di convalida dei livelli](#TroubleshootingValidation)

- [Individuare e risolvere gli errori di convalida dei livelli](#UnderstandingValidationErrors)

## <a name="see-if-an-item-supports-validation"></a><a name="SupportsValidation"></a> Verificare se un elemento supporta la convalida
 È possibile collegare i livelli a siti Web, documenti Office, file di testo normale e file in progetti condivisi tra più app, ma il processo di convalida non li includerà. Gli errori di convalida non verranno visualizzati per i riferimenti a progetti oppure a assembly collegati a livelli separati quando tra tali livelli non è presente alcuna dipendenza. Tali riferimenti non vengono considerati dipendenze a meno che il codice non li usi.

1. Nel diagramma livello selezionare uno o più livelli, fare clic con il pulsante destro del mouse sulla selezione e quindi scegliere **Visualizza collegamenti**.

2. In **Esplora livello**esaminare la colonna **supporta la convalida** . Se il valore è false, l'elemento non supporta la convalida.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a><a name="IncludeReferences"></a> Includi altri assembly e progetti .NET per la convalida
 Quando si trascinano elementi nel diagramma livello, i riferimenti agli assembly .NET o ai progetti corrispondenti vengono aggiunti automaticamente alla cartella **Riferimenti livello** nel progetto di modello. Questa cartella contiene i riferimenti agli assembly e ai progetti analizzati durante la convalida. È possibile includere altri assembly e progetti .NET per la convalida senza trascinarli manualmente nel diagramma livello.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto di modello o sulla cartella **Riferimenti livello** , quindi scegliere **Aggiungi riferimento**.

2. Nella finestra di dialogo **Aggiungi riferimento** selezionare gli assembly o i progetti, quindi fare clic su **OK**.

## <a name="validate-code-manually"></a><a name="ValidateManually"></a> Convalidare manualmente il codice
 Se si dispone di un diagramma livello aperto collegato a elementi della soluzione, è possibile eseguire il comando **Validate** Shortcut dal diagramma. È anche possibile usare il prompt dei comandi per eseguire il comando **MSBuild** con la proprietà personalizzata **/p: ValidateArchitecture** impostata su **true**. Ad esempio, analogamente alle modifiche nel codice, eseguire regolarmente la convalida dei livelli in modo da rilevare tempestivamente conflitti di dipendenza.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Per convalidare il codice da un diagramma livello aperto

1. Fare clic con il pulsante destro del mouse sulla superficie del diagramma, quindi scegliere **convalida architettura**.

    > [!NOTE]
    > Per impostazione predefinita, la proprietà **azione di compilazione** nel file del diagramma livello (con estensione layerdiagram) è impostata su **convalida** , in modo che il diagramma venga incluso nel processo di convalida.

     La finestra **Elenco errori** segnala gli eventuali errori che si verificano. Per ulteriori informazioni sugli errori di convalida, vedere [comprendere e risolvere gli errori di convalida dei livelli](#UnderstandingValidationErrors).

2. Per visualizzare l'origine di ogni errore, fare doppio clic sull'errore nella finestra **Elenco errori** .

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] potrebbe visualizzare una mappa codice anziché l'origine dell'errore. Ciò si verifica quando il codice presenta una dipendenza in un assembly che non è specificata nel diagramma livello o quando al codice manca una dipendenza specificata nel diagramma livello. Esaminare la mappa del codice o il codice per determinare se la dipendenza deve esistere. Per altre informazioni sulle mappe codice, vedere [eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md).

3. Per gestire gli errori, vedere [gestire gli errori di convalida](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>Per convalidare il codice al prompt dei comandi

1. Aprire il prompt dei comandi di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

2. Selezionare una delle opzioni seguenti:

   - Per convalidare il codice rispetto a un progetto di modellazione specifico nella soluzione, eseguire [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la seguente proprietà personalizzata.

     ```
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
     ```

     - - oppure -

       Passare alla cartella contenente il file di progetto di modellazione (con estensione modelproj) e il diagramma livello, quindi eseguire [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la seguente proprietà personalizzata.

     ```
     msbuild /p:ValidateArchitecture=true
     ```

   - Per convalidare il codice rispetto a tutti i progetti di modello nella soluzione, eseguire [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la seguente proprietà personalizzata:

     ```
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
     ```

     - - oppure -

       Individuare la cartella della soluzione che deve contenere un progetto di modellazione che a sua volta contiene un diagramma livello, quindi eseguire [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la seguente proprietà personalizzata.

     ```
     msbuild /p:ValidateArchitecture=true
     ```

     Verranno elencati tutti gli errori che si verificano. Per altre informazioni su [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , vedere attività [MSBuild](../msbuild/msbuild.md) e [MSBuild](../msbuild/msbuild-task.md).

   Per ulteriori informazioni sugli errori di convalida, vedere [comprendere e risolvere gli errori di convalida dei livelli](#UnderstandingValidationErrors).

### <a name="manage-validation-errors"></a><a name="ManageErrors"></a> Gestione degli errori di convalida
 Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è buona norma registrare un elemento di lavoro in [!INCLUDE[esprfound](../includes/esprfound-md.md)].

> [!WARNING]
> Per creare un elemento di lavoro o aggiungere un collegamento ad esso, è necessario essere già connessi al controllo del codice sorgente TFS. Se si prova ad aprire una connessione in un'istanza diversa del controllo del codice sorgente TFS, Visual Studio chiude automaticamente la soluzione corrente. Prima di provare a creare un elemento di lavoro o ad aggiungervi un collegamento, verificare di essere già connessi all'istanza appropriata del controllo del codice sorgente. Nelle versioni successive di Visual Studio, i comandi di menu non sono disponibili se non si è connessi a un'istanza del controllo del codice sorgente.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>Per creare un elemento di lavoro per un errore di convalida

- Nella finestra di **Elenco errori** , fare clic con il pulsante destro del mouse sull'errore, scegliere **Crea elemento di lavoro**, quindi fare clic sul tipo di elemento di lavoro che si desidera creare.

  Usare queste attività per gestire gli errori di convalida nella finestra **Elenco errori** :

|**To**|**Attenersi alla seguente procedura**|
|------------|----------------------------|
|Eliminare gli errori selezionati durante la convalida|Fare clic con il pulsante destro del mouse su uno o più errori selezionati, scegliere **Gestisci errori di convalida**, quindi fare clic su non **visualizzare errori**.<br /><br /> Gli errori eliminati vengono visualizzati come barrati. Alla successiva convalida, questi errori non saranno visualizzati.<br /><br /> Gli errori eliminati vengono registrati in un file con estensione suppressions per il file del diagramma livello corrispondente.|
|Interrompere l'eliminazione di errori selezionati|Fare clic con il pulsante destro del mouse sull'errore o sugli errori eliminati selezionati, scegliere **Gestisci errori di convalida**, quindi fare clic su **Interrompi eliminazione errori**.<br /><br /> Alla successiva convalida, gli errori eliminati selezionati verranno visualizzati.|
|Ripristinare tutti gli errori eliminati nella finestra di **Elenco errori**|Fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra **Elenco errori** , scegliere **Gestisci errori di convalida**, quindi fare clic su **Mostra tutti gli errori eliminati**.|
|Nascondi tutti gli errori eliminati dalla finestra di **Elenco errori**|Fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra **Elenco errori** , scegliere **Gestisci errori di convalida**, quindi fare clic su **Nascondi tutti gli errori eliminati**.|

## <a name="validate-code-automatically"></a><a name="ValidateAuto"></a> Convalidare automaticamente il codice
 È possibile eseguire la convalida dei livelli ogni volta che si esegue una compilazione. Se il team utilizza Team Foundation Build, è possibile eseguire la convalida dei livelli nelle archiviazioni gestite, che si possono specificare creando un'attività personalizzata MSBuild, e utilizzare i rapporti di compilazione per raccogliere gli errori di convalida. Per creare compilazioni di archiviazione gestita, vedere [usare un processo di compilazione di archiviazione gestita per convalidare le modifiche](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>Per convalidare automaticamente il codice durante una compilazione locale

- Usare un editor di testo per aprire il file del progetto di modello (.modelproj), quindi includere la proprietà seguente:

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- - oppure -

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto di modello che contiene il diagramma livello o i diagrammi, quindi scegliere **Proprietà**.

2. Nella finestra **Proprietà** impostare la proprietà **convalida architettura** del progetto di modello su **true**.

    Il progetto di modello viene incluso nel processo di convalida.

3. In **Esplora soluzioni**fare clic sul file del diagramma livello (con estensione layerdiagram) che si desidera utilizzare per la convalida.

4. Nella finestra **Proprietà** verificare che la proprietà **azione di compilazione** del diagramma sia impostata su **convalida**.

    Il diagramma livello viene incluso nel processo di convalida.

   Per gestire gli errori nella finestra di Elenco errori, vedere [gestire gli errori di convalida](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Per convalidare codice automaticamente durante un'operazione di Team Foundation Build

1. In **Team Explorer**fare doppio clic sulla definizione di compilazione, quindi scegliere **elabora**.

2. In **Parametri processo di compilazione**espandere **compilazione**e digitare quanto segue nel parametro **Argomenti MSBuild** :

    `/p:ValidateArchitecture=true`

   Per ulteriori informazioni sugli errori di convalida, vedere [comprendere e risolvere gli errori di convalida dei livelli](#UnderstandingValidationErrors). Per altre informazioni su [!INCLUDE[esprbuild](../includes/esprbuild-md.md)], vedere:

- [Compilare l'applicazione](/azure/devops/pipelines/index)

- [Utilizzare il modello predefinito per il processo di compilazione](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [Modificare una compilazione legacy basata su UpgradeTemplate. XAML](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [Personalizzare il modello del processo di compilazione](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Monitorare lo stato di una compilazione in esecuzione](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="troubleshoot-layer-validation-issues"></a><a name="TroubleshootingValidation"></a> Risolvere i problemi di convalida dei livelli
 Nella tabella seguente vengono descritti i problemi di convalida dei livelli e la relativa risoluzione. Questi problemi differiscono dagli errori risultanti da conflitti tra il codice e la progettazione. Per ulteriori informazioni su questi errori, vedere [comprendere e risolvere gli errori di convalida dei livelli](#UnderstandingValidationErrors).

|**Problema**|**Possibili cause**|**Risoluzione**|
|---------------|------------------------|--------------------|
|Gli errori di convalida non si verificano come previsto.|La convalida non funziona sui diagrammi livello copiati da altri diagrammi livello in Esplora soluzioni e appartenenti allo stesso progetto di modellazione. I diagrammi livello copiati in questo modo contengono gli stessi riferimenti del diagramma livello originale.|Aggiungere un nuovo diagramma livello al progetto di modellazione.<br /><br /> Copiare gli elementi dal diagramma livello di origine al nuovo diagramma.|

## <a name="understanding-and-resolving-layer-validation-errors"></a><a name="UnderstandingValidationErrors"></a> Informazioni e risoluzione degli errori di convalida dei livelli
 Quando si esegue la convalida di codice in base a un diagramma livello, se il codice è in conflitto con la progettazione si verificano errori di convalida. In presenza delle condizioni seguenti è possibile ad esempio che si verifichino errori di convalida:

- Un artefatto viene assegnato al livello errato. In questo caso, spostare l'elemento.

- Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.

  Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. È possibile eseguire questa attività in modo iterativo.

  Nella sezione seguente viene descritta la sintassi usata negli errori, viene illustrato il significato degli errori e vengono indicate le operazioni che è possibile eseguire per risolverli o gestirli.

|**Sintassi**|**Descrizione**|
|----------------|---------------------|
|*Artefatto*(*tipoelementon*)|*Artefatto* è un artefatto associato a un livello nel diagramma livello.<br /><br /> *Tipoelementon* è il tipo di *artefatto*, ad esempio una **classe** o un **Metodo**, ad esempio:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metodo)|
|*NomeSpazioDeiNomiN*|Nome di uno spazio dei nomi.|
|*NomeLivelloN*|Nome di un livello nel diagramma livello.|
|*TipoDipendenza*|Tipo di relazione di dipendenza tra *elemento1* e *Artifact2*. Ad esempio, *elemento1* ha una relazione **calls** con *Artifact2*.|

|**Sintassi errore**|**Descrizione errore**|
|----------------------|---------------------------|
|AV0001: dipendenza non valida: *elemento1*(*tipoartefatto1*)--> *Artifact2*(*tipoartefatto2*)<br /><br /> Livelli: *LayerName1*, *LayerName2* &#124; dipendenze: *DependencyType*|*Elemento1* in *LayerName1* non deve avere una dipendenza da *Artifact2* in *LayerName2* perché *LayerName1* non ha una dipendenza diretta da *LayerName2*.|
|AV1001: spazio dei nomi non valido: *artefatto*<br /><br /> Livello: *layername* &#124; spazio dei nomi richiesto: *Nomespaziodeinomi1* &#124; spazio dei nomi corrente: *nomespaziodeinomi2*|Per *LayerName* è necessario che gli elementi associati appartengano a *nomespaziodeinomi1*. L' *artefatto* è in *nomespaziodeinomi2*, non in *nomespaziodeinomi1*.|
|AV1002: dipende dallo spazio dei nomi non consentito: *elemento1*(*Tipoartefatto1*) &#124; *Artifact2*(*tipoartefatto2*)<br /><br /> Livello: *layername* &#124; spazio dei nomi non consentito: *NamespaceName* &#124; dipendenze: *DependencyType*|Per *LayerName* è necessario che gli elementi associati non dipendano da *NamespaceName*. *Elemento1* non può dipendere da *Artifact2* perché *Artifact2* è in *NamespaceName*.|
|AV1003: nello spazio dei nomi non consentito: *artefatto*(*ArtifactType*)<br /><br /> Livello: *layername* &#124; spazio dei nomi non consentito: *NamespaceName*|Per *LayerName* è necessario che gli elementi associati non possano appartenere allo *spazio dei nomi*. L' *elemento* appartiene a *NamespaceName*.|
|AV3001: collegamento mancante: il livello '*LayerName*' si collega a'*artefatto*' che non è stato trovato. Probabilmente manca un riferimento a un assembly.|*LayerName* si collega a un elemento che non è stato trovato. Ad esempio, è possibile che manchi un collegamento a una classe perché nel progetto di modellazione manca un riferimento all'assembly che contiene la classe.|
|AV9001: errori interni durante l'analisi dell'architettura. I risultati potrebbero non essere completi. Per altre informazioni, vedere il log dettagliato degli eventi di compilazione o la finestra di output.|Per altre informazioni, vedere il log degli eventi di compilazione o la finestra di output.|

## <a name="security"></a>Sicurezza

## <a name="see-also"></a>Vedere anche
 [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)
