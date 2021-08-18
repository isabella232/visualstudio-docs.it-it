---
title: Convalidare il codice con i diagrammi delle dipendenze
description: Per assicurarsi che il codice non sia in conflitto con la progettazione, è consigliabile convalidare il codice con i diagrammi delle dipendenze in Visual Studio.
ms.custom: SEO-VS-2020
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 3bb9aeadd0e511ce5ed770eb56f0a2f02bf26542
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123515"
---
# <a name="validate-code-with-dependency-diagrams"></a>Convalidare il codice con i diagrammi delle dipendenze

## <a name="why-use-dependency-diagrams"></a>Perché usare i diagrammi delle dipendenze?

Per assicurarsi che il codice non sia in conflitto con la progettazione, convalidare il codice con i diagrammi delle dipendenze in Visual Studio. In questo modo è possibile effettuare le operazioni seguenti:

- Trovare i conflitti tra le dipendenze nel codice e le dipendenze nel diagramma delle dipendenze.

- Trovare le dipendenze sulle quali potrebbero influire le modifiche proposte.

   Ad esempio, è possibile modificare il diagramma delle dipendenze per visualizzare le potenziali modifiche all'architettura e quindi convalidare il codice per visualizzare le dipendenze interessate.

- Effettuare il refactoring o la migrazione del codice in una progettazione diversa.

   Trovare codice o dipendenze che richiedono azioni quando si sposta il codice in un'architettura diversa.

**Requisiti**

- Visual Studio

  Per creare un diagramma delle dipendenze per un progetto .NET Core, è necessario Visual Studio 2019 versione 16.2 o successiva.

- Soluzione con un progetto di modellazione con un diagramma delle dipendenze. Questo diagramma delle dipendenze deve essere collegato agli elementi in C# o Visual Basic da convalidare. Vedere [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md).

Per informazioni su quali edizioni di Visual Studio questa funzionalità, vedere Supporto dell'edizione per gli strumenti di [architettura e modellazione](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

È possibile convalidare manualmente il codice da un diagramma delle dipendenze aperto in Visual Studio o da un prompt dei comandi. È anche possibile convalidare automaticamente il codice quando si eseguono compilazioni locali o Azure Pipelines compilazioni. Vedere [Channel 9 Video: Progettare e convalidare l'architettura usando i diagrammi delle dipendenze.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)

> [!IMPORTANT]
> Se si vuole eseguire la convalida dei livelli usando Team Foundation Server (TFS), è necessario installare anche la stessa versione di Visual Studio nel server di compilazione.

## <a name="live-dependency-validation"></a>Convalida delle dipendenze in tempo reale

La convalida delle dipendenze viene eseguita in tempo reale e gli errori vengono visualizzati immediatamente **nell'Elenco errori**.

* La convalida in tempo reale è supportata per C# e Visual Basic.

* Per abilitare l'analisi completa della soluzione quando si usa la convalida delle dipendenze in tempo reale, aprire le impostazioni delle opzioni dalla barra dorata visualizzata in **Elenco errori**.

  - È possibile ignorare definitivamente la barra dorata se non si è interessati a visualizzare tutti i problemi di architettura nella soluzione.
  - Se non si abilita l'analisi completa della soluzione, l'analisi viene eseguita solo per i file modificati.

* Quando si aggiornano i progetti per abilitare la convalida in tempo reale, viene visualizzata una finestra di dialogo che mostra lo stato di avanzamento della conversione.

* Quando si aggiorna un progetto per la convalida delle dipendenze in tempo reale, la versione del pacchetto NuGet viene aggiornata in modo che sia la stessa per tutti i progetti ed è la versione più recente in uso.

* L'aggiunta di un nuovo progetto di convalida delle dipendenze attiva un aggiornamento del progetto.

## <a name="see-if-an-item-supports-validation"></a>Vedere se un elemento supporta la convalida

È possibile collegare livelli a siti Web, Office documenti, file di testo normale e file in progetti condivisi tra più app, ma il processo di convalida non li include. Gli errori di convalida non verranno visualizzati per i riferimenti a progetti oppure a assembly collegati a livelli separati quando tra tali livelli non è presente alcuna dipendenza. Tali riferimenti non vengono considerati dipendenze a meno che il codice non li usi.

1. Nel diagramma delle dipendenze selezionare uno o più livelli, fare clic con il pulsante destro del mouse sulla selezione e quindi scegliere **Visualizza collegamenti**.

2. In **Esplora livelli** esaminare la colonna Supporto **convalida.** Se il valore è false, l'elemento non supporta la convalida.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Includere altri progetti e assembly .NET per la convalida

Quando si trascinano elementi nel diagramma delle dipendenze, i riferimenti agli assembly o ai progetti .NET corrispondenti vengono aggiunti automaticamente alla cartella **Riferimenti** livello nel progetto di modellazione. Questa cartella contiene i riferimenti agli assembly e ai progetti analizzati durante la convalida. È possibile includere altri assembly e progetti .NET per la convalida senza trascinarli manualmente nel diagramma delle dipendenze.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di modellazione o sulla cartella **Riferimenti livello** e quindi scegliere Aggiungi **riferimento**.

2. Nella finestra **di dialogo Aggiungi** riferimento selezionare gli assembly o i progetti e quindi fare clic su **OK.**

## <a name="validate-code-manually"></a>Convalidare manualmente il codice

Se si dispone di un diagramma delle dipendenze aperto  collegato agli elementi della soluzione, è possibile eseguire il comando Convalida collegamento dal diagramma. È anche possibile usare il prompt dei comandi per eseguire il **comando msbuild** con la proprietà personalizzata **/p:ValidateArchitecture** impostata su **True.** Ad esempio, analogamente alle modifiche nel codice, eseguire regolarmente la convalida dei livelli in modo da rilevare tempestivamente conflitti di dipendenza.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Convalidare il codice da un diagramma delle dipendenze aperto

1. Fare clic con il pulsante destro del mouse sulla superficie del diagramma e quindi **scegliere Convalida architettura**.

    > [!NOTE]
    > Per impostazione predefinita, **la** proprietà Azione di compilazione nel file di diagramma delle dipendenze (con estensione layerdiagram) è impostata su **Convalida** in modo che il diagramma sia incluso nel processo di convalida.

     La **finestra Elenco** errori segnala eventuali errori che si verificano. Per altre informazioni sugli errori di convalida, vedere [Risolvere i problemi di convalida dei livelli.](#troubleshoot-layer-validation-issues)

2. Per visualizzare l'origine di ogni errore, fare doppio clic sull'errore nella **finestra Elenco** errori.

    > [!NOTE]
    > Visual Studio possibile visualizzare una mappa del codice anziché l'origine dell'errore. Ciò si verifica quando il codice ha una dipendenza da un assembly non specificato dal diagramma delle dipendenze oppure nel codice manca una dipendenza specificata dal diagramma delle dipendenze. Esaminare la mappa del codice o il codice per determinare se la dipendenza deve esistere. Per altre informazioni sulle mappe codice, vedere [Eseguire il mapping delle dipendenze tra le soluzioni](../modeling/map-dependencies-across-your-solutions.md).

3. Per gestire gli errori, vedere [Risolvere gli errori di convalida dei livelli](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Convalidare il codice al prompt dei comandi

1. Aprire il prompt Visual Studio comandi.

2. Selezionare una delle opzioni seguenti:

   - Per convalidare il codice rispetto a un progetto di modellazione specifico nella soluzione, eseguire MSBuild con la proprietà personalizzata seguente.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - - oppure -

       Passare alla cartella che contiene il file del progetto di modellazione (con estensione modelproj) e il diagramma delle dipendenze e quindi eseguire MSBuild con la proprietà personalizzata seguente:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Per convalidare il codice in base a tutti i progetti di modellazione nella soluzione, eseguire MSBuild con la proprietà personalizzata seguente:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - - oppure -

       Passare alla cartella della soluzione, che deve contenere un progetto di modellazione contenente un diagramma delle dipendenze, quindi eseguire MSBuild con la proprietà personalizzata seguente:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Verranno elencati tutti gli errori che si verificano. Per altre informazioni sui MSBuild, [vedere](../msbuild/msbuild.md) MSBuild e [MSBuild Task](../msbuild/msbuild-task.md).

   Per altre informazioni sugli errori di convalida, vedere [Risolvere i problemi di convalida dei livelli.](#troubleshoot-layer-validation-issues)

### <a name="manage-validation-errors"></a>Gestire gli errori di convalida

Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è consigliabile registrare un elemento di lavoro in Team Foundation.

> [!WARNING]
> Per creare un elemento di lavoro o aggiungere un collegamento ad esso, è necessario essere già connessi al controllo del codice sorgente TFS. Se si prova ad aprire una connessione in un'istanza diversa del controllo del codice sorgente TFS, Visual Studio chiude automaticamente la soluzione corrente. Prima di provare a creare un elemento di lavoro o ad aggiungervi un collegamento, verificare di essere già connessi all'istanza appropriata del controllo del codice sorgente. Nelle versioni successive di Visual Studio, i comandi di menu non sono disponibili se non si è connessi a un'istanza del controllo del codice sorgente.

#### <a name="create-a-work-item-for-a-validation-error"></a>Creare un elemento di lavoro per un errore di convalida

- Nella finestra **Elenco errori fare** clic con il pulsante destro del mouse sull'errore, scegliere **Crea** elemento di lavoro e quindi fare clic sul tipo di elemento di lavoro che si vuole creare.

Usare queste attività per gestire gli errori di convalida nella **finestra Elenco** errori:

|**To**|**seguire le operazioni di seguito riportate**|
|-|-|
|Eliminare gli errori selezionati durante la convalida|Fare clic con il pulsante destro del mouse su uno o più errori selezionati, scegliere Gestisci errori **di convalida** e quindi fare clic su **Elimina errori**.<br /><br /> Gli errori eliminati vengono visualizzati come barrati. Alla successiva convalida, questi errori non saranno visualizzati.<br /><br /> Gli errori eliminati vengono rilevati in un file con estensione suppressions per il file del diagramma delle dipendenze corrispondente.|
|Interrompere l'eliminazione di errori selezionati|Fare clic con il pulsante destro del mouse sull'errore o gli errori eliminati selezionati, scegliere Gestisci errori **di** convalida e quindi fare clic su **Arresta eliminazione errori**.<br /><br /> Alla successiva convalida, gli errori eliminati selezionati verranno visualizzati.|
|Ripristinare tutti gli errori eliminati nella **finestra Elenco** errori|Fare clic con il pulsante destro **del** mouse in un punto qualsiasi della finestra Elenco errori, scegliere Gestisci errori **di** convalida e quindi fare clic su Mostra tutti gli **errori eliminati**.|
|Nascondere tutti gli errori eliminati dalla **finestra Elenco** errori|Fare clic con il pulsante destro **del** mouse in un punto qualsiasi della finestra Elenco errori, scegliere Gestisci errori **di** convalida e quindi fare clic su Nascondi tutti gli **errori eliminati**.|

## <a name="validate-code-automatically"></a>Convalidare automaticamente il codice

È possibile eseguire la convalida dei livelli ogni volta che si esegue una compilazione. Se il team usa Azure DevOps, è possibile eseguire la convalida dei livelli con le archiviazioni controllate, che è possibile specificare creando un'attività MSBuild personalizzata e usare report di compilazione per raccogliere gli errori di convalida. Per creare compilazioni di archiviazione controllate, vedere Archiviazione con controllo con controllo [TFVC](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Per convalidare automaticamente il codice durante una compilazione locale

Usare un editor di testo per aprire il file del progetto di modello (.modelproj), quindi includere la proprietà seguente:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- - oppure -

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di modellazione che contiene il diagramma delle dipendenze o i diagrammi, quindi scegliere **Proprietà.**

2. Nella finestra **Proprietà** impostare la proprietà Convalida architettura del progetto di **modellazione** su **True.**

    Il progetto di modello viene incluso nel processo di convalida.

3. Nella Esplora soluzioni fare clic sul file di diagramma delle dipendenze (con **estensione** layerdiagram) che si vuole usare per la convalida.

4. Nella finestra **Proprietà** verificare che la  proprietà Azione di compilazione del diagramma sia impostata su **Convalida.**

    È incluso il diagramma delle dipendenze nel processo di convalida.

Per gestire gli errori nella finestra Elenco errori, vedere Risolvere [gli errori di convalida dei livelli.](#resolve-layer-validation-errors)

## <a name="troubleshoot-layer-validation-issues"></a>Risolvere i problemi di convalida dei livelli

Nella tabella seguente vengono descritti i problemi di convalida dei livelli e la relativa risoluzione. Questi problemi differiscono dagli errori risultanti da conflitti tra il codice e la progettazione. Per altre informazioni su questi errori, vedere Risolvere i problemi [di convalida dei livelli.](#troubleshoot-layer-validation-issues)

|**Problema**|**Possibile causa**|**Risoluzione**|
|-|-|-|
|Gli errori di convalida non si verificano come previsto.|La convalida non funziona nei diagrammi delle dipendenze copiati da altri diagrammi delle dipendenze in Esplora soluzioni e che si nello stesso progetto di modellazione. I diagrammi delle dipendenze copiati in questo modo contengono gli stessi riferimenti del diagramma delle dipendenze originale.|Aggiungere un nuovo diagramma delle dipendenze al progetto di modellazione.<br /><br /> Copiare gli elementi dal diagramma delle dipendenze di origine nel nuovo diagramma.|

## <a name="resolve-layer-validation-errors"></a>Risolvere gli errori di convalida dei livelli

Quando si convalida il codice rispetto a un diagramma delle dipendenze, si verificano errori di convalida quando il codice è in conflitto con la progettazione. In presenza delle condizioni seguenti è possibile ad esempio che si verifichino errori di convalida:

- Un artefatto viene assegnato al livello errato. In questo caso, spostare l'elemento.

- Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.

Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. È possibile eseguire questa attività in modo iterativo.

Nella sezione seguente viene descritta la sintassi usata negli errori, viene illustrato il significato degli errori e vengono indicate le operazioni che è possibile eseguire per risolverli o gestirli.

|**Sintassi**|**Descrizione**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* è un artefatto associato a un livello nel diagramma delle dipendenze.<br /><br /> *ArtifactTypeN* è il tipo di *ArtifactN,* ad esempio **una classe** o **un metodo,** ad esempio:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metodo)|
|*NomeSpazioDeiNomiN*|Nome di uno spazio dei nomi.|
|*NomeLivelloN*|Nome di un livello nel diagramma delle dipendenze.|
|*TipoDipendenza*|Tipo di relazione di dipendenza tra *Artifact1* e *Artifact2.* Ad esempio, *Artifact1 ha* una **relazione Calls** con *Artifact2*.|

| **Sintassi errore** | **Descrizione dell'errore** |
|-|-|
| DV0001: **Dipendenza non valida** | Questo problema viene segnalato quando un elemento di codice (spazio dei nomi, tipo, membro) mappato a un livello fa riferimento a un elemento di codice mappato a un altro livello, ma non esiste alcuna freccia di dipendenza tra questi livelli nel diagramma di convalida delle dipendenze contenente questi livelli. Si tratta di una violazione del vincolo di dipendenza. |
| DV1001: nome **dello spazio dei nomi non valido** | Questo problema viene segnalato su un elemento di codice associato a un livello la cui proprietà "Allowed Namespace Names" non contiene lo spazio dei nomi in cui è definito questo elemento di codice. Si tratta di una violazione del vincolo di denominazione. Si noti che la sintassi di "Nomi di spazio dei nomi consentiti" deve essere un elenco di spazi dei nomi con punto e virgola in cui è consentito definire gli elementi di codice associati a . |
| DV1002: dipendenza **da uno spazio dei nomi senza riferimenti** | Questo problema viene segnalato su un elemento di codice associato a un livello e fa riferimento a un altro elemento di codice definito in uno spazio dei nomi definito nella proprietà "Spazio dei nomi non referenziabile" del livello. Si tratta di una violazione del vincolo di denominazione. Si noti che la proprietà "Spazi dei nomi non referenziabili" è definita come elenco di spazi dei nomi separati da punto e virgola a cui non è necessario fare riferimento negli elementi di codice associati a questo livello. |
| DV1003: **nome dello spazio dei nomi non consentito** | Questo problema viene segnalato su un elemento di codice associato a un livello la cui proprietà "Nomi di spazio dei nomi non consentiti" contiene lo spazio dei nomi in cui è definito questo elemento di codice. Si tratta di una violazione del vincolo di denominazione. Si noti che la proprietà "Nome spazio dei nomi non consentito" è definita come un elenco di spazi dei nomi separati da punto e virgola in cui non devono essere definiti gli elementi di codice associati a questo livello. |
| DV2001: **presenza di diagrammi livello** | Questo problema viene segnalato in un progetto che non include un file di diagramma delle dipendenze, ma fa riferimento agli analizzatori di convalida delle dipendenze. Se la convalida delle dipendenze non è stata usata, è possibile rimuovere "Microsoft.DependencyValidation.Analyzers" direttamente dal Esplora soluzioni o eliminare questo avviso. Per aggiungere un diagramma delle [dipendenze, vedere Creare diagrammi delle dipendenze dal codice.](../modeling/create-layer-diagrams-from-your-code.md) |
| DV2002: **base tipi non mappati** | Questo problema viene segnalato quando non viene eseguito il mapping di un elemento di codice ad alcun livello. |
| DV3001: **collegamento mancante** | Il livello '*LayerName*' è collegato a '*Artifact*' che non è possibile trovare. Probabilmente manca un riferimento a un assembly. |
| DV9001: **l'analisi dell'architettura ha rilevato errori interni** | I risultati potrebbero non essere completi. Per altre informazioni, vedere il log dettagliato degli eventi di compilazione o la finestra di output. |

## <a name="see-also"></a>Vedi anche

- [Convalida delle dipendenze in tempo reale in Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)
- [Video: Convalidare le dipendenze dell'architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
