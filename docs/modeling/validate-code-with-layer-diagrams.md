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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6286c787b1f69c0e44541e156b06440c7267f79d
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57870360"
---
# <a name="validate-code-with-dependency-diagrams"></a>Convalidare il codice con i diagrammi delle dipendenze

## <a name="why-use-dependency-diagrams"></a>Perché usare i diagrammi delle dipendenze?

Per assicurarsi che non entrino in conflitto con la progettazione codice, è possibile convalidare il codice con diagrammi delle dipendenze in Visual Studio. In questo modo è possibile effettuare le operazioni seguenti:

- Trovare conflitti tra dipendenze nel codice e dipendenze nel diagramma delle dipendenze.

- Trovare le dipendenze sulle quali potrebbero influire le modifiche proposte.

   Ad esempio, è possibile modificare il diagramma delle dipendenze per mostrare potenziali modifiche all'architettura e quindi convalidare il codice per visualizzare le dipendenze interessate.

- Effettuare il refactoring o la migrazione del codice in una progettazione diversa.

   Trovare codice o dipendenze che richiedono azioni quando si sposta il codice in un'architettura diversa.

**Requisiti**

- Visual Studio

- Una soluzione che include un progetto di modellazione con un diagramma delle dipendenze. Questo diagramma di dipendenza deve essere collegato agli artefatti nei progetti C# o Visual Basic che si desidera convalidare. Visualizzare [creare i diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md).

> [!NOTE]
> I diagrammi delle dipendenze non sono supportati per i progetti .NET Core in Visual Studio.

Per informazioni su quali edizioni di Visual Studio supportano questa funzionalità, vedere [supporto di edizione per un'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

È possibile convalidare il codice manualmente da un diagramma di dipendenze open in Visual Studio o da un prompt dei comandi. È inoltre possibile convalidare codice automaticamente quando si eseguono compilazioni locali o le pipeline di Azure Build. Vedere [Video di Channel 9: Progettare e convalidare l'architettura utilizzando i diagrammi delle dipendenze](http://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Se si desidera eseguire la convalida dei livelli tramite Team Foundation Server (TFS), è necessario installare anche la stessa versione di Visual Studio nel server di compilazione.

## <a name="live-dependency-validation"></a>Convalida delle dipendenze in tempo reale

Convalida della dipendenza si verifica in tempo reale e gli errori vengono visualizzati immediatamente nella **elenco errori**.

* Convalida in tempo reale è supportata per C# e Visual Basic.

* Per abilitare l'analisi della soluzione completa quando si usa la convalida live delle dipendenze, aprire le impostazioni delle opzioni da barra color oro che viene visualizzato nei **elenco errori**.

   - Se non si è interessati a visualizzare tutti i problemi dell'architettura della soluzione, è possibile ignorare in modo permanente la barra color oro.
   - Se non si abilita analisi della soluzione completa, l'analisi viene eseguita solo per i file modificati.

* Quando si aggiornano progetti per attivare la convalida in tempo reale, una finestra di dialogo Mostra lo stato di avanzamento della conversione.

* Quando si aggiorna un progetto per la convalida delle dipendenze in tempo reale, la versione del pacchetto NuGet viene aggiornata in modo da essere uguale per tutti i progetti ed è la versione più recente in uso.

* Aggiunta di una nuova dipendenza convalida progetto i trigger un aggiornamento del progetto.

## <a name="see-if-an-item-supports-validation"></a>Vedere se un elemento supporta la convalida

È possibile collegare livelli a siti Web, documenti Office, file di testo normale e file in progetti condivisi tra più App, ma il processo di convalida non li includerà. Gli errori di convalida non verranno visualizzati per i riferimenti a progetti oppure a assembly collegati a livelli separati quando tra tali livelli non è presente alcuna dipendenza. Tali riferimenti non vengono considerati dipendenze a meno che il codice non li usi.

1.  Nel diagramma delle dipendenze, selezionare uno o più livelli, fare doppio clic la selezione e quindi fare clic su **Visualizza collegamenti**.

2.  Nelle **Esplora livello**, esaminare le **supporta la convalida** colonna. Se il valore è false, l'elemento non supporta la convalida.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Includere altri progetti e assembly .NET per la convalida

Quando si trascinano elementi nel diagramma delle dipendenze, vengono aggiunti automaticamente a riferimenti a progetti o assembly .NET corrispondente di **riferimenti livello** cartella nel progetto di modellazione. Questa cartella contiene i riferimenti agli assembly e ai progetti analizzati durante la convalida. È possibile includere altri assembly e progetti .NET per la convalida senza trascinarli manualmente nel diagramma delle dipendenze.

1.  Nelle **Esplora soluzioni**, fare clic sul progetto di modellazione o il **riferimenti livello** cartella e quindi fare clic su **Aggiungi riferimento**.

2.  Nel **Aggiungi riferimento** della finestra di dialogo selezionare gli assembly o i progetti e quindi fare clic su **OK**.

## <a name="validate-code-manually"></a>Convalidare manualmente il codice

Se si dispone di un diagramma di dipendenza aperto collegato agli elementi della soluzione, è possibile eseguire la **Validate** comando di scelta rapida del diagramma. È anche possibile usare il prompt dei comandi per eseguire la **msbuild** con il **ValidateArchitecture** proprietà personalizzata impostata su **True**. Ad esempio, analogamente alle modifiche nel codice, eseguire regolarmente la convalida dei livelli in modo da rilevare tempestivamente conflitti di dipendenza.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Convalidare il codice da un diagramma di dipendenze open

1.  Pulsante destro del mouse sulla superficie del diagramma e quindi fare clic su **Convalida architettura**.

    > [!NOTE]
    > Per impostazione predefinita, il **Build Action** sul file di diagramma (con estensione layerdiagram) delle dipendenze è impostata su **Validate** in modo che il diagramma è incluso nel processo di convalida.

     Il **elenco errori** finestra segnala tutti gli errori che si verificano. Per altre informazioni sugli errori di convalida, vedere [risolvere i problemi di convalida dei layer](#troubleshoot-layer-validation-issues).

2.  Per visualizzare l'origine di ogni errore, fare doppio clic su errore nel **elenco errori** finestra.

    > [!NOTE]
    > Visual Studio potrebbe essere visualizzata una mappa codice anziché l'origine dell'errore. Ciò si verifica quando il codice presenta una dipendenza da un assembly che non è specificato nel diagramma delle dipendenze o codice manca una dipendenza specificata nel diagramma delle dipendenze. Esaminare la mappa del codice o il codice per determinare se la dipendenza deve esistere. Per altre informazioni sulle mappe del codice, vedere [mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md).

3.  Per gestire gli errori, vedere [risolvere gli errori di convalida dei layer](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Convalidare il codice al prompt dei comandi

1. Aprire il prompt dei comandi di Visual Studio.

2. Effettuare una delle seguenti operazioni:

   - Per convalidare il codice rispetto a un progetto di modellazione specifico nella soluzione, eseguire MSBuild con la seguente proprietà personalizzata.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - oppure -

       Passare alla cartella che contiene il progetto di modellazione (con estensione modelproj) file e la dipendenza del diagramma e quindi eseguire MSBuild con la seguente proprietà personalizzata:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Per convalidare codice rispetto a tutti i progetti di modellazione nella soluzione, eseguire MSBuild con la seguente proprietà personalizzata:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - oppure -

       Passare alla cartella della soluzione, che deve contenere un progetto di modellazione contenente un diagramma delle dipendenze, quindi eseguire MSBuild con la seguente proprietà personalizzata:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Verranno elencati tutti gli errori che si verificano. Per altre informazioni su MSBuild, vedere [MSBuild](../msbuild/msbuild.md) e [attività MSBuild](../msbuild/msbuild-task.md).

   Per altre informazioni sugli errori di convalida, vedere [risolvere i problemi di convalida dei layer](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Gestire gli errori di convalida

Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è buona norma registrare un elemento di lavoro in Team Foundation.

> [!WARNING]
> Per creare un elemento di lavoro o aggiungere un collegamento ad esso, è necessario essere già connessi al controllo del codice sorgente TFS. Se si prova ad aprire una connessione in un'istanza diversa del controllo del codice sorgente TFS, Visual Studio chiude automaticamente la soluzione corrente. Prima di provare a creare un elemento di lavoro o ad aggiungervi un collegamento, verificare di essere già connessi all'istanza appropriata del controllo del codice sorgente. Nelle versioni successive di Visual Studio, i comandi di menu non sono disponibili se non si è connessi a un'istanza del controllo del codice sorgente.

#### <a name="create-a-work-item-for-a-validation-error"></a>Creare un elemento di lavoro per un errore di convalida

- Nel **elenco errori** finestra, fare doppio clic su errore, scegliere **Crea elemento di lavoro**e quindi scegliere il tipo di elemento di lavoro che si desidera creare.

Usare queste attività per gestire gli errori di convalida nel **elenco errori** finestra:

|**Per**|**Seguire questi passaggi**|
|-|-|
|Eliminare gli errori selezionati durante la convalida|Fare doppio clic su uno o più errori selezionati, scegliere **Gestisci errori di convalida**, quindi fare clic su **Elimina errori**.<br /><br /> Gli errori eliminati vengono visualizzati come barrati. Alla successiva convalida, questi errori non saranno visualizzati.<br /><br /> Gli errori eliminati vengono registrati in un file con estensione suppressions per il corrispondente file di diagramma delle dipendenze.|
|Interrompere l'eliminazione di errori selezionati|Fare doppio clic su selezionato eliminati gli errori, scegliere **Gestisci errori di convalida**, quindi fare clic su **Interrompi eliminazione errori**.<br /><br /> Alla successiva convalida, gli errori eliminati selezionati verranno visualizzati.|
|Ripristinare tutti gli errori eliminati nella **elenco errori** finestra|Fare doppio clic in un punto qualsiasi nella **elenco errori** finestra, scegliere **Gestisci errori di convalida**, quindi fare clic su **Mostra tutti gli errori eliminati**.|
|Tutti gli errori eliminati da nascondere il **elenco errori** finestra|Fare doppio clic in un punto qualsiasi nella **elenco errori** finestra, scegliere **Gestisci errori di convalida**, quindi fare clic su **Nascondi errori eliminati**.|

## <a name="validate-code-automatically"></a>Convalidare automaticamente il codice

È possibile eseguire la convalida dei livelli ogni volta che si esegue una compilazione. Se il team Usa DevOps di Azure, è possibile eseguire la convalida dei livelli con archiviazioni gestite, che si possono specificare creando un'attività personalizzata MSBuild e usare i report di compilazione per raccogliere gli errori di convalida. Per creare compilazioni di archiviazione gestite, vedere [TFVC l'archiviazione gestita](/azure/devops/pipelines/build/triggers#gated).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Per convalidare automaticamente il codice durante una compilazione locale

Usare un editor di testo per aprire il file del progetto di modello (.modelproj), quindi includere la proprietà seguente:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- oppure -

1.  Nelle **Esplora soluzioni**, fare clic sul progetto che contiene il diagramma delle dipendenze o i diagrammi di modellazione e quindi fare clic su **proprietà**.

2.  Nel **delle proprietà** finestra, impostare il progetto di modellazione **Convalida architettura** proprietà **True**.

    Il progetto di modello viene incluso nel processo di convalida.

3.  Nelle **Esplora soluzioni**, fare clic sul file di diagramma (con estensione layerdiagram) delle dipendenze che si desidera utilizzare per la convalida.

4.  Nel **proprietà** finestra, assicurarsi che il diagramma **azione di compilazione** viene impostata su **Validate**.

    Ciò include il diagramma delle dipendenze nel processo di convalida.

Per gestire gli errori nella finestra Elenco errori, vedere [risolvere gli errori di convalida dei layer](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Risolvere i problemi di convalida dei livelli

Nella tabella seguente vengono descritti i problemi di convalida dei livelli e la relativa risoluzione. Questi problemi differiscono dagli errori risultanti da conflitti tra il codice e la progettazione. Per altre informazioni su questi errori, vedere [risolvere i problemi di convalida dei layer](#troubleshoot-layer-validation-issues).

|**Problema**|**Causa possibile**|**Risoluzione**|
|-|-|-|
|Gli errori di convalida non si verificano come previsto.|Convalida non funziona sui diagrammi delle dipendenze che vengono copiati da altri diagrammi delle dipendenze in Esplora soluzioni e che si trovano nello stesso progetto di modello. i diagrammi delle dipendenze che vengono copiati in questo modo contengono gli stessi riferimenti del diagramma di dipendenza originale.|Aggiungere un nuovo diagramma di dipendenza al progetto di modellazione.<br /><br /> Copiare gli elementi dal diagramma di dipendenza di origine al nuovo diagramma.|

## <a name="resolve-layer-validation-errors"></a>Risolvere gli errori di convalida dei layer

Durante la convalida di codice in base a un diagramma delle dipendenze, si verificano errori di convalida quando il codice è in conflitto con la progettazione. In presenza delle condizioni seguenti è possibile ad esempio che si verifichino errori di convalida:

- Un elemento viene assegnato al livello errato. In questo caso, spostare l'elemento.

- Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.

Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. È possibile eseguire questa attività in modo iterativo.

Nella sezione seguente viene descritta la sintassi usata negli errori, viene illustrato il significato degli errori e vengono indicate le operazioni che è possibile eseguire per risolverli o gestirli.

|**Sintassi**|**Descrizione**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*Elementon* è un elemento che è associato a un livello nel diagramma delle dipendenze.<br /><br /> *Tipoelementon* è il tipo di *Elementon*, ad esempio un **classe** oppure **metodo**, ad esempio:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metodo)|
|*NamespaceNameN*|Nome di uno spazio dei nomi.|
|*LayerNameN*|Il nome di un livello nel diagramma delle dipendenze.|
|*DependencyType*|Il tipo di relazione di dipendenza tra *Elemento1* e *elemento2*. Ad esempio, *Elemento1* ha una **chiamate** relazione con *elemento2*.|

| **Sintassi errore** | **Descrizione dell'errore** |
|-|-|
| DV0001: **Dipendenza non valida** | Questo problema viene segnalato quando un elemento di codice (spazio dei nomi, tipo, membro) mappato a un riferimento di livello un elemento di codice mappato a un altro livello, ma non vi è alcuna freccia di dipendenza tra questi livelli nel diagramma di convalida delle dipendenze che contiene questo livelli. Si tratta di una violazione di vincolo di dipendenza. |
| DV1001: **Nome dello spazio dei nomi non valido** | Questo problema viene segnalato in un elemento di codice associato a un livello che la proprietà "Consentito Namespace Names" non contiene lo spazio dei nomi in cui è definito questo elemento di codice. Si tratta di una violazione dei vincoli di denominazione. Si noti che la sintassi di "Consentiti nomi Namespace" deve essere un elenco di punti e virgola degli spazi dei nomi in cui il codice gli elementi associati sono livello sono consentite da definire. |
| DV1002: **Dipendenza da spazi dello spazio dei nomi** | Questo problema viene segnalato in un elemento di codice associati a un livello e che fanno riferimento a un altro elemento di codice definito in uno spazio dei nomi che viene definito nella proprietà "Namespace spazi" del livello. Si tratta di una violazione dei vincoli di denominazione. Si noti che la proprietà "Spazi dei nomi" è definita come un elenco separato da punti e virgola degli spazi dei nomi che non deve essere fatto riferimento negli elementi di codice associati a questo livello. |
| DV1003: **Nome dello spazio dei nomi non consentito** | Questo problema viene segnalato in un elemento di codice associato a un livello che "Non consentiti nomi Namespace" proprietà contiene lo spazio dei nomi in cui è definito questo elemento di codice. Si tratta di una violazione dei vincoli di denominazione. Si noti che la proprietà "Nome spazio dei nomi non consentito" è definita come un elenco separato da punti e virgola degli spazi dei nomi in cui il codice non devono essere definiti gli elementi associati a questo livello. |
| DV3001: **Collegamento mancante** | Livello '*nomelivello*'Collega a'*artefatto*' che non viene trovato. Probabilmente manca un riferimento a un assembly. |
| DV9001: **Analisi dell'architettura trovati gli errori interni** | I risultati potrebbero non essere completi. Per altre informazioni, vedere il log dettagliato degli eventi di compilazione o la finestra di output. |

## <a name="see-also"></a>Vedere anche

- [Convalida Live delle dipendenze in Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)
- [Video: Convalidare le dipendenze dell'architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)