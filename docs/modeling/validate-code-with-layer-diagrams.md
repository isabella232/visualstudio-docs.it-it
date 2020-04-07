---
title: Convalidare il codice con i diagrammi delle dipendenze
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 975fe8eac5657e245027a4811e50bbc93528cfe5
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759695"
---
# <a name="validate-code-with-dependency-diagrams"></a>Convalidare il codice con i diagrammi delle dipendenze

## <a name="why-use-dependency-diagrams"></a>Perché usare i diagrammi di dipendenza?

Per assicurarsi che il codice non sia in conflitto con la progettazione, convalidare il codice con i diagrammi di dipendenza in Visual Studio.To make sure that code doesn't conflict with its design, validate your code with dependency diagrams in Visual Studio. In questo modo è possibile effettuare le operazioni seguenti:

- Trova i conflitti tra le dipendenze nel codice e le dipendenze nel diagramma di dipendenza.

- Trovare le dipendenze sulle quali potrebbero influire le modifiche proposte.

   Ad esempio, è possibile modificare il diagramma di dipendenza per mostrare le potenziali modifiche all'architettura e quindi convalidare il codice per visualizzare le dipendenze interessate.

- Effettuare il refactoring o la migrazione del codice in una progettazione diversa.

   Trovare codice o dipendenze che richiedono azioni quando si sposta il codice in un'architettura diversa.

**Requisiti**

- Visual Studio

  Per creare un diagramma di dipendenza per un progetto .NET Core, è necessario disporre di Visual Studio 2019 versione 16.2 o successiva.

- Soluzione con un progetto di modellazione con un diagramma di dipendenza. Questo diagramma di dipendenza deve essere collegato agli elementi nei progetti di Visual Basic o C, che si desidera convalidare. Consultate [Creare diagrammi di dipendenza dal codice.](../modeling/create-layer-diagrams-from-your-code.md)

Per sapere quali edizioni di Visual Studio supportano questa funzionalità, vedere [Supporto dell'edizione per gli strumenti](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)di architettura e modellazione .

È possibile convalidare il codice manualmente da un diagramma di dipendenza aperto in Visual Studio o da un prompt dei comandi. È anche possibile convalidare automaticamente il codice quando si eseguono compilazioni locali o compilazioni di Azure Pipelines.You can also validate code automatically when running local builds or Azure Pipelines builds. Vedere [Channel 9 Video: Progettare e convalidare l'architettura utilizzando i diagrammi di dipendenza.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)

> [!IMPORTANT]
> Se si desidera eseguire la convalida dei livelli utilizzando Team Foundation Server (TFS), è necessario installare anche la stessa versione di Visual Studio nel server di compilazione.

## <a name="live-dependency-validation"></a>Convalida delle dipendenze in tempo reale

La convalida delle dipendenze viene eseguita in tempo reale e gli errori vengono visualizzati immediatamente **nell'Elenco errori**.

* La convalida in tempo reale è supportata per C .NET e Visual Basic.

* Per abilitare l'analisi completa della soluzione quando si utilizza la convalida delle dipendenze dinamiche, aprire le impostazioni delle opzioni dalla barra d'oro visualizzata **nell'Elenco errori**.

  - È possibile ignorare definitivamente la barra d'oro se non si è interessati a vedere tutti i problemi architettonici nella soluzione.
  - Se non si abilita l'analisi completa della soluzione, l'analisi viene eseguita solo per i file in fase di modifica.

* Quando si aggiornano i progetti per abilitare la convalida in tempo reale, una finestra di dialogo mostra l'avanzamento della conversione.

* Quando si aggiorna un progetto per la convalida delle dipendenze dinamiche, la versione del pacchetto NuGet viene aggiornata per essere la stessa per tutti i progetti ed è la versione più recente in uso.

* L'aggiunta di un nuovo progetto di convalida delle dipendenze attiva un aggiornamento del progetto.

## <a name="see-if-an-item-supports-validation"></a>Vedere se un elemento supporta la convalida

È possibile collegare i livelli a siti Web, documenti di Office, file di testo normale e file in progetti condivisi tra più app, ma il processo di convalida non li includerà. Gli errori di convalida non verranno visualizzati per i riferimenti a progetti oppure a assembly collegati a livelli separati quando tra tali livelli non è presente alcuna dipendenza. Tali riferimenti non vengono considerati dipendenze a meno che il codice non li usi.

1. Nel diagramma di dipendenza selezionare uno o più layer, fare clic con il pulsante destro del mouse sulla selezione e quindi **scegliere Visualizza collegamenti**.

2. In **Esplora layer**esaminare la colonna Supporta la **convalida** . Se il valore è false, l'elemento non supporta la convalida.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Includere altri progetti e assembly .NET per la convalida

Quando si trascinano elementi nel diagramma di dipendenza, i riferimenti agli assembly o ai progetti .NET corrispondenti vengono aggiunti automaticamente alla cartella **Riferimenti livello** nel progetto di modellazione. Questa cartella contiene i riferimenti agli assembly e ai progetti analizzati durante la convalida. È possibile includere altri assembly e progetti .NET per la convalida senza trascinarli manualmente nel diagramma delle dipendenze.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto di modellazione o sulla cartella **Riferimenti layer,** quindi **scegliere Aggiungi riferimento**.

2. Nella finestra di dialogo **Aggiungi riferimento** selezionare gli assembly o i progetti e quindi fare clic su **OK**.

## <a name="validate-code-manually"></a>Convalidare manualmente il codice

Se si dispone di un diagramma di dipendenza aperto collegato agli elementi della soluzione, è possibile eseguire il comando **Convalida** collegamento dal diagramma. È inoltre possibile utilizzare il prompt dei comandi per eseguire il comando **msbuild** con la proprietà personalizzata **/p:ValidateArchitecture** impostata su **True**. Ad esempio, analogamente alle modifiche nel codice, eseguire regolarmente la convalida dei livelli in modo da rilevare tempestivamente conflitti di dipendenza.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Convalidare il codice da un diagramma di dipendenza apertoValidate code from an open dependency diagram

1. Fare clic con il pulsante destro del mouse sulla superficie del diagramma e quindi **scegliere Convalida architettura**.

    > [!NOTE]
    > Per impostazione predefinita, la proprietà **Operazione** di compilazione nel file del diagramma di dipendenza (.layerdiagram) è impostata su **Convalida** in modo che il diagramma venga incluso nel processo di convalida.

     La finestra **Elenco errori** segnala eventuali errori che si verificano. Per ulteriori informazioni sugli errori di convalida, consultate Risolvere i problemi di [convalida dei layer.](#troubleshoot-layer-validation-issues)

2. Per visualizzare l'origine di ogni errore, fare doppio clic sull'errore nella finestra **Elenco errori.**

    > [!NOTE]
    > Visual Studio potrebbe visualizzare una mappa del codice anziché l'origine dell'errore. Ciò si verifica quando il codice ha una dipendenza da un assembly che non è specificato dal diagramma di dipendenza o nel codice manca una dipendenza specificata dal diagramma di dipendenza. Esaminare la mappa del codice o il codice per determinare se la dipendenza deve esistere. Per ulteriori informazioni sulle mappe del codice, vedere [Eseguire il mapping delle dipendenze tra le soluzioni.](../modeling/map-dependencies-across-your-solutions.md)

3. Per gestire gli errori, consultate Risolvere gli errori di [convalida dei livelli.](#resolve-layer-validation-errors)

### <a name="validate-code-at-the-command-prompt"></a>Convalidare il codice al prompt dei comandi

1. Aprire il prompt dei comandi di Visual Studio.Open the Visual Studio command prompt.

2. Selezionare una delle opzioni seguenti:

   - Per convalidare il codice in base a un progetto di modellazione specifico nella soluzione, eseguire MSBuild con la proprietà personalizzata seguente.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - - oppure -

       Passare alla cartella che contiene il file di progetto di modellazione (con estensione modelproj) e il diagramma di dipendenza, quindi eseguire MSBuild con la proprietà personalizzata seguente:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Per convalidare il codice in base a tutti i progetti di modellazione nella soluzione, eseguire MSBuild con la proprietà personalizzata seguente:To validate code against all modeling projects in the solution, run MSBuild with the following custom property:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - - oppure -

       Passare alla cartella della soluzione, che deve contenere un progetto di modellazione contenente un diagramma di dipendenza, quindi eseguire MSBuild con la proprietà personalizzata seguente:Browse to the solution folder, which must contain a modeling project that contains a dependency diagram, and then run MSBuild with the following custom property:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Verranno elencati tutti gli errori che si verificano. Per altre informazioni su MSBuild, vedere [MSBuild](../msbuild/msbuild.md) e [MSBuild Task](../msbuild/msbuild-task.md).

   Per ulteriori informazioni sugli errori di convalida, consultate Risolvere i problemi di [convalida dei layer.](#troubleshoot-layer-validation-issues)

### <a name="manage-validation-errors"></a>Gestire gli errori di convalida

Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è consigliabile registrare un elemento di lavoro in Team Foundation.

> [!WARNING]
> Per creare un elemento di lavoro o aggiungere un collegamento ad esso, è necessario essere già connessi al controllo del codice sorgente TFS. Se si prova ad aprire una connessione in un'istanza diversa del controllo del codice sorgente TFS, Visual Studio chiude automaticamente la soluzione corrente. Prima di provare a creare un elemento di lavoro o ad aggiungervi un collegamento, verificare di essere già connessi all'istanza appropriata del controllo del codice sorgente. Nelle versioni successive di Visual Studio, i comandi di menu non sono disponibili se non si è connessi a un'istanza del controllo del codice sorgente.

#### <a name="create-a-work-item-for-a-validation-error"></a>Creare un elemento di lavoro per un errore di convalidaCreate a work item for a validation error

- Nella finestra **Elenco errori** fare clic con il pulsante destro del mouse sull'errore, scegliere Crea elemento di **lavoro**, quindi fare clic sul tipo di elemento di lavoro che si desidera creare.

Utilizzare queste attività per gestire gli errori di convalida nella finestra **Elenco errori:Use** these tasks to manage validation errors in the Error List window:

|**A**|**Attenersi alla seguente procedura**|
|-|-|
|Eliminare gli errori selezionati durante la convalida|Fare clic con il pulsante destro del mouse su uno o più errori selezionati, **scegliere Gestisci errori**di convalida e quindi fare clic su Elimina **errori**.<br /><br /> Gli errori eliminati vengono visualizzati come barrati. Alla successiva convalida, questi errori non saranno visualizzati.<br /><br /> Gli errori soppressi vengono rilevati in un file .suppressions per il file di diagramma dipendenze corrispondente.|
|Interrompere l'eliminazione di errori selezionati|Fare clic con il pulsante destro del mouse sugli errori o sugli errori eliminati selezionati, **scegliere Gestisci errori**di convalida , quindi fare clic su Interrompi errori di **eliminazione**.<br /><br /> Alla successiva convalida, gli errori eliminati selezionati verranno visualizzati.|
|Ripristinare tutti gli errori soppressi nella finestra **Elenco errori**|Fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra **Elenco errori,** **scegliere Gestisci errori**di convalida , quindi fare clic su Mostra tutti gli **errori soppressi**.|
|Nascondi tutti gli errori soppressi dalla finestra **Elenco errori**|Fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra **Elenco errori,** **scegliere Gestisci errori**di convalida , quindi fare clic su Nascondi tutti gli **errori soppressi**.|

## <a name="validate-code-automatically"></a>Convalidare automaticamente il codice

È possibile eseguire la convalida dei livelli ogni volta che si esegue una compilazione. Se il team usa DevOps di Azure, è possibile eseguire la convalida dei livelli con archiviazioni gestite, che è possibile specificare creando un'attività MSBuild personalizzata, e usare i report di compilazione per raccogliere gli errori di convalida. Per creare compilazioni di archiviazione gated, vedere [TFVC gated check-in](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Per convalidare automaticamente il codice durante una compilazione locale

Usare un editor di testo per aprire il file del progetto di modello (.modelproj), quindi includere la proprietà seguente:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- - oppure -

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto di modellazione contenente il diagramma di dipendenza o i diagrammi, quindi scegliere **Proprietà**.

2. Nella finestra **Proprietà** impostare la proprietà **Convalida architettura** del progetto di modellazione su **True**.

    Il progetto di modello viene incluso nel processo di convalida.

3. In **Esplora soluzioni**fare clic sul file del diagramma di dipendenza (con estensione layerdiagram) che si desidera utilizzare per la convalida.

4. Nella finestra **Proprietà** verificare che la proprietà **Operazione** di compilazione del diagramma sia impostata su **Convalida**.

    Ciò include il diagramma di dipendenza nel processo di convalida.

Per gestire gli errori nella finestra Elenco errori, consultate Risolvere gli errori di [convalida dei livelli.](#resolve-layer-validation-errors)

## <a name="troubleshoot-layer-validation-issues"></a>Risolvere i problemi di convalida dei livelli

Nella tabella seguente vengono descritti i problemi di convalida dei livelli e la relativa risoluzione. Questi problemi differiscono dagli errori risultanti da conflitti tra il codice e la progettazione. Per ulteriori informazioni su questi errori, consultate Risolvere i problemi di [convalida dei layer.](#troubleshoot-layer-validation-issues)

|**Problema**|**Possibile causa**|**Risoluzione**|
|-|-|-|
|Gli errori di convalida non si verificano come previsto.|La convalida non funziona nei diagrammi di dipendenza copiati da altri diagrammi di dipendenza in Esplora soluzioni e che si trovano nello stesso progetto di modellazione. i diagrammi di dipendenza copiati in questo modo contengono gli stessi riferimenti del diagramma di dipendenza originale.|Aggiungere un nuovo diagramma di dipendenza al progetto di modellazione.<br /><br /> Copiare gli elementi dal diagramma di dipendenza di origine al nuovo diagramma.|

## <a name="resolve-layer-validation-errors"></a>Risolvere gli errori di convalida dei livelli

Quando si convalida il codice rispetto a un diagramma di dipendenza, si verificano errori di convalida quando il codice è in conflitto con la progettazione. In presenza delle condizioni seguenti è possibile ad esempio che si verifichino errori di convalida:

- Un artefatto viene assegnato al livello errato. In questo caso, spostare l'elemento.

- Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.

Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. È possibile eseguire questa attività in modo iterativo.

Nella sezione seguente viene descritta la sintassi usata negli errori, viene illustrato il significato degli errori e vengono indicate le operazioni che è possibile eseguire per risolverli o gestirli.

|**Sintassi**|**Descrizione**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* è un elemento associato a un livello nel diagramma di dipendenza.<br /><br /> *ArtifactTypeN* è il tipo di *ArtifactN*, ad esempio un **class** o **un metodo**, ad esempio:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metodo)|
|*NomeSpazioDeiNomiN*|Nome di uno spazio dei nomi.|
|*NomeLivelloN*|Nome di un livello nel diagramma di dipendenza.|
|*TipoDipendenza*|Tipo di relazione di dipendenza tra *Artifact1* e *Artifact2*. Ad esempio, *Artifact1* ha una relazione **Calls** con *Artifact2*.|

| **Sintassi errore** | **Descrizione dell'errore** |
|-|-|
| DV0001: **dipendenza non valida** | Questo problema viene segnalato quando un elemento di codice (spazio dei nomi, tipo, membro) mappato a un livello fa riferimento a un elemento di codice mappato a un altro livello, ma non esiste alcuna freccia di dipendenza tra questi livelli nel diagramma di convalida delle dipendenze contenente questi livelli. Si tratta di una violazione del vincolo di dipendenza. |
| DV1001: **nome dello spazio dei nomi non valido** | Questo problema viene segnalato in un elemento di codice associato a un livello che "Nomi dello spazio dei nomi consentiti" proprietà non contiene lo spazio dei nomi in cui è definito questo elemento di codice. Si tratta di una violazione del vincolo di denominazione. Si noti che la sintassi di "Nomi dello spazio dei nomi consentiti" deve essere un elenco di punti e virgola di spazi dei nomi in cui è consentito definire gli elementi di codice associati a layer. |
| DV1002: **Dipendenza dallo spazio dei nomi non a cui non è possibile fare riferimento** | Questo problema viene segnalato su un elemento di codice associato a un livello e fa riferimento a un altro elemento di codice definito in uno spazio dei nomi definito nella proprietà "Spazio dei nomi non referenziabile" del livello. Si tratta di una violazione del vincolo di denominazione. Si noti che la proprietà "Unreferenceable Namespaces" è definita come un elenco separato da punti e virgola di spazi dei nomi a cui non deve essere fatto riferimento negli elementi di codice associati a questo livello. |
| DV1003: **Nome dello spazio dei nomi non consentito** | Questo problema viene segnalato in un elemento di codice associato a un livello che la proprietà "Nomi dello spazio dei nomi non consentiti" contiene lo spazio dei nomi in cui è definito questo elemento di codice. Si tratta di una violazione del vincolo di denominazione. Si noti che la proprietà "Nome spazio dei nomi non consentito" è definita come un elenco separato da punti e virgola di spazi dei nomi in cui gli elementi di codice associati a questo livello non devono essere definiti. |
| DV2001: **presenza diagramma a livello** | Questo problema viene segnalato in un progetto che non include un file di diagramma di dipendenza, ma fa riferimento agli analizzatori di convalida delle dipendenze. Se la convalida delle dipendenze non è stata utilizzata, è possibile rimuovere "Microsoft.DependencyValidation.Analyzers" direttamente da Esplora soluzioni o eliminare questo avviso. Per aggiungere un diagramma di dipendenza, vedere [Creare diagrammi di dipendenza dal codice.](../modeling/create-layer-diagrams-from-your-code.md) |
| DV2002: **Base sui tipi non mappati** | Questo problema viene segnalato quando un elemento di codice non è mappato ad alcun livello. |
| DV3001: **Collegamento mancante** | Il livello '*LayerName*' si collega a '*Artefatto*' che non è possibile trovare. Probabilmente manca un riferimento a un assembly. |
| DV9001: **L'analisi architettonica ha rilevato errori interni** | I risultati potrebbero non essere completi. Per altre informazioni, vedere il log dettagliato degli eventi di compilazione o la finestra di output. |

## <a name="see-also"></a>Vedere anche

- [Convalida delle dipendenze attive in Visual StudioLive dependency validation in Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)
- [Video: Convalidare le dipendenze dell'architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
