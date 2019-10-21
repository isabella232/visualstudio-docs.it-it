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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a2b972c3c275f3e43819220532ac0a3c4a597e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662931"
---
# <a name="validate-code-with-dependency-diagrams"></a>Convalidare il codice con i diagrammi delle dipendenze

## <a name="why-use-dependency-diagrams"></a>Perché usare i diagrammi di dipendenza?

Per assicurarsi che il codice non sia in conflitto con la progettazione, convalidare il codice con i diagrammi di dipendenza in Visual Studio. In questo modo è possibile effettuare le operazioni seguenti:

- Individuare i conflitti tra le dipendenze nel codice e le dipendenze nel diagramma delle dipendenze.

- Trovare le dipendenze sulle quali potrebbero influire le modifiche proposte.

   Ad esempio, è possibile modificare il diagramma delle dipendenze per mostrare le potenziali modifiche all'architettura e quindi convalidare il codice per visualizzare le dipendenze interessate.

- Effettuare il refactoring o la migrazione del codice in una progettazione diversa.

   Trovare codice o dipendenze che richiedono azioni quando si sposta il codice in un'architettura diversa.

**Requirements**

- Visual Studio

  Per creare un diagramma delle dipendenze per un progetto .NET Core, è necessario disporre di Visual Studio 2019 versione 16,2 o successiva.

- Soluzione che dispone di un progetto di modello con un diagramma delle dipendenze. Questo diagramma di dipendenza deve essere collegato a elementi in C# o Visual Basic progetti che si desidera convalidare. Vedere [creare diagrammi di dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md).

Per visualizzare le edizioni di Visual Studio che supportano questa funzionalità, vedere [supporto dell'edizione per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

È possibile convalidare manualmente il codice da un diagramma delle dipendenze aperto in Visual Studio o da un prompt dei comandi. È anche possibile convalidare automaticamente il codice quando si eseguono compilazioni locali o Azure Pipelines compilazioni. Vedere [video di Channel 9: progettare e convalidare l'architettura usando i diagrammi delle dipendenze](http://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Se si desidera eseguire la convalida dei livelli utilizzando Team Foundation Server (TFS), è necessario installare anche la stessa versione di Visual Studio nel server di compilazione.

## <a name="live-dependency-validation"></a>Convalida delle dipendenze in tempo reale

La convalida delle dipendenze viene eseguita in tempo reale e gli errori vengono visualizzati immediatamente nel **Elenco errori**.

* La convalida in tempo reale C# è supportata per e Visual Basic.

* Per abilitare l'analisi della soluzione completa quando si usa la convalida delle dipendenze in tempo reale, aprire le impostazioni delle opzioni dalla barra dorata visualizzata nella **Elenco errori**.

  - Se non si è interessati a visualizzare tutti i problemi di architettura nella soluzione, è possibile chiudere definitivamente la barra dorata.
  - Se non si Abilita l'analisi della soluzione completa, l'analisi viene eseguita solo per i file modificati.

* Quando si aggiornano i progetti per abilitare la convalida in tempo reale, in una finestra di dialogo viene visualizzato lo stato della conversione.

* Quando si aggiorna un progetto per la convalida delle dipendenze in tempo reale, la versione del pacchetto NuGet viene aggiornata in modo che corrisponda a tutti i progetti ed è la versione più recente in uso.

* L'aggiunta di un nuovo progetto di convalida delle dipendenze attiva un aggiornamento del progetto.

## <a name="see-if-an-item-supports-validation"></a>Vedere se un elemento supporta la convalida

È possibile collegare i livelli a siti Web, documenti Office, file di testo normale e file in progetti condivisi tra più app, ma il processo di convalida non li includerà. Gli errori di convalida non verranno visualizzati per i riferimenti a progetti oppure a assembly collegati a livelli separati quando tra tali livelli non è presente alcuna dipendenza. Tali riferimenti non vengono considerati dipendenze a meno che il codice non li usi.

1. Nel diagramma delle dipendenze selezionare uno o più livelli, fare clic con il pulsante destro del mouse sulla selezione e quindi scegliere **Visualizza collegamenti**.

2. In **Esplora livello**esaminare la colonna **supporta la convalida** . Se il valore è false, l'elemento non supporta la convalida.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Includere altri progetti e assembly .NET per la convalida

Quando si trascinano elementi nel diagramma delle dipendenze, i riferimenti agli assembly .NET o ai progetti corrispondenti vengono aggiunti automaticamente alla cartella **Riferimenti livello** nel progetto di modello. Questa cartella contiene i riferimenti agli assembly e ai progetti analizzati durante la convalida. È possibile includere altri assembly e progetti .NET per la convalida senza trascinarli manualmente nel diagramma delle dipendenze.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto di modello o sulla cartella **Riferimenti livello** , quindi scegliere **Aggiungi riferimento**.

2. Nella finestra di dialogo **Aggiungi riferimento** selezionare gli assembly o i progetti, quindi fare clic su **OK**.

## <a name="validate-code-manually"></a>Convalidare manualmente il codice

Se si dispone di un diagramma delle dipendenze aperto collegato a elementi della soluzione, è possibile eseguire il comando **Validate** Shortcut dal diagramma. È anche possibile usare il prompt dei comandi per eseguire il comando **MSBuild** con la proprietà personalizzata **/p: ValidateArchitecture** impostata su **true**. Ad esempio, analogamente alle modifiche nel codice, eseguire regolarmente la convalida dei livelli in modo da rilevare tempestivamente conflitti di dipendenza.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Convalidare il codice da un diagramma delle dipendenze aperto

1. Fare clic con il pulsante destro del mouse sulla superficie del diagramma, quindi scegliere **convalida architettura**.

    > [!NOTE]
    > Per impostazione predefinita, la proprietà **azione di compilazione** nel file di diagramma delle dipendenze (con estensione layerdiagram) è impostata su **convalida** , in modo che il diagramma venga incluso nel processo di convalida.

     La finestra **Elenco errori** segnala gli eventuali errori che si verificano. Per ulteriori informazioni sugli errori di convalida, vedere [risolvere i problemi di convalida dei livelli](#troubleshoot-layer-validation-issues).

2. Per visualizzare l'origine di ogni errore, fare doppio clic sull'errore nella finestra **Elenco errori** .

    > [!NOTE]
    > Visual Studio potrebbe visualizzare una mappa codice anziché l'origine dell'errore. Questo errore si verifica quando il codice presenta una dipendenza da un assembly non specificato dal diagramma delle dipendenze oppure nel codice manca una dipendenza specificata dal diagramma delle dipendenze. Esaminare la mappa del codice o il codice per determinare se la dipendenza deve esistere. Per altre informazioni sulle mappe codice, vedere [eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md).

3. Per gestire gli errori, vedere [risolvere gli errori di convalida del livello](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Convalidare il codice al prompt dei comandi

1. Aprire il prompt dei comandi di Visual Studio.

2. Effettuare una delle seguenti operazioni:

   - Per convalidare il codice rispetto a un progetto di modello specifico nella soluzione, eseguire MSBuild con la seguente proprietà personalizzata.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - oppure -

       Individuare la cartella che contiene il file del progetto di modello (con estensione modelproj) e il diagramma delle dipendenze, quindi eseguire MSBuild con la seguente proprietà personalizzata:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Per convalidare il codice rispetto a tutti i progetti di modellazione nella soluzione, eseguire MSBuild con la seguente proprietà personalizzata:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - oppure -

       Individuare la cartella della soluzione che deve contenere un progetto di modello contenente un diagramma delle dipendenze, quindi eseguire MSBuild con la seguente proprietà personalizzata:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Verranno elencati tutti gli errori che si verificano. Per altre informazioni su MSBuild [, vedere attività MSBuild e](../msbuild/msbuild.md) [MSBuild](../msbuild/msbuild-task.md).

   Per ulteriori informazioni sugli errori di convalida, vedere [risolvere i problemi di convalida dei livelli](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Gestire gli errori di convalida

Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è consigliabile registrare un elemento di lavoro in Team Foundation.

> [!WARNING]
> Per creare un elemento di lavoro o aggiungere un collegamento ad esso, è necessario essere già connessi al controllo del codice sorgente TFS. Se si prova ad aprire una connessione in un'istanza diversa del controllo del codice sorgente TFS, Visual Studio chiude automaticamente la soluzione corrente. Prima di provare a creare un elemento di lavoro o ad aggiungervi un collegamento, verificare di essere già connessi all'istanza appropriata del controllo del codice sorgente. Nelle versioni successive di Visual Studio, i comandi di menu non sono disponibili se non si è connessi a un'istanza del controllo del codice sorgente.

#### <a name="create-a-work-item-for-a-validation-error"></a>Creare un elemento di lavoro per un errore di convalida

- Nella finestra di **Elenco errori** , fare clic con il pulsante destro del mouse sull'errore, scegliere **Crea elemento di lavoro**, quindi fare clic sul tipo di elemento di lavoro che si desidera creare.

Usare queste attività per gestire gli errori di convalida nella finestra **Elenco errori** :

|**Per**|**Attenersi alla seguente procedura**|
|-|-|
|Eliminare gli errori selezionati durante la convalida|Fare clic con il pulsante destro del mouse su uno o più errori selezionati, scegliere **Gestisci errori di convalida**, quindi fare clic su non **visualizzare errori**.<br /><br /> Gli errori eliminati vengono visualizzati come barrati. Alla successiva convalida, questi errori non saranno visualizzati.<br /><br /> Gli errori eliminati vengono rilevati in un file con estensione eliminazioni per il file del diagramma di dipendenza corrispondente.|
|Interrompere l'eliminazione di errori selezionati|Fare clic con il pulsante destro del mouse sull'errore o sugli errori eliminati selezionati, scegliere **Gestisci errori di convalida**, quindi fare clic su **Interrompi eliminazione errori**.<br /><br /> Alla successiva convalida, gli errori eliminati selezionati verranno visualizzati.|
|Ripristinare tutti gli errori eliminati nella finestra di **Elenco errori**|Fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra **Elenco errori** , scegliere **Gestisci errori di convalida**, quindi fare clic su **Mostra tutti gli errori eliminati**.|
|Nascondi tutti gli errori eliminati dalla finestra di **Elenco errori**|Fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra **Elenco errori** , scegliere **Gestisci errori di convalida**, quindi fare clic su **Nascondi tutti gli errori eliminati**.|

## <a name="validate-code-automatically"></a>Convalidare automaticamente il codice

È possibile eseguire la convalida dei livelli ogni volta che si esegue una compilazione. Se il team USA Azure DevOps, è possibile eseguire la convalida dei livelli con le archiviazioni gestite, che è possibile specificare creando un'attività MSBuild personalizzata e usare i report di compilazione per raccogliere gli errori di convalida. Per creare compilazioni di archiviazione gestita, vedere [archiviazione gestita di TFVC](/azure/devops/pipelines/build/triggers#gated).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Per convalidare automaticamente il codice durante una compilazione locale

Usare un editor di testo per aprire il file del progetto di modello (.modelproj), quindi includere la proprietà seguente:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- oppure -

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto di modello contenente il diagramma o i diagrammi delle dipendenze, quindi scegliere **Proprietà**.

2. Nella finestra **Proprietà** impostare la proprietà **convalida architettura** del progetto di modello su **true**.

    Il progetto di modello viene incluso nel processo di convalida.

3. In **Esplora soluzioni**fare clic sul file del diagramma di dipendenza (con estensione layerdiagram) che si desidera utilizzare per la convalida.

4. Nella finestra **Proprietà** verificare che la proprietà **azione di compilazione** del diagramma sia impostata su **convalida**.

    Questo include il diagramma delle dipendenze nel processo di convalida.

Per gestire gli errori nella finestra di Elenco errori, vedere [risolvere gli errori di convalida dei livelli](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Risolvere i problemi di convalida dei livelli

Nella tabella seguente vengono descritti i problemi di convalida dei livelli e la relativa risoluzione. Questi problemi differiscono dagli errori risultanti da conflitti tra il codice e la progettazione. Per ulteriori informazioni su questi errori, vedere [risolvere i problemi di convalida dei livelli](#troubleshoot-layer-validation-issues).

|**Problema**|**Possibili cause**|**Risoluzione**|
|-|-|-|
|Gli errori di convalida non si verificano come previsto.|La convalida non funziona sui diagrammi delle dipendenze copiati da altri diagrammi di dipendenza in Esplora soluzioni e che si trovano nello stesso progetto di modello. i diagrammi delle dipendenze che vengono copiati in questo modo contengono gli stessi riferimenti del diagramma di dipendenza originale.|Aggiungere un nuovo diagramma delle dipendenze al progetto di modello.<br /><br /> Copiare gli elementi dal diagramma delle dipendenze di origine al nuovo diagramma.|

## <a name="resolve-layer-validation-errors"></a>Risolvere gli errori di convalida del livello

Quando si convalida il codice in base a un diagramma di dipendenza, si verificano errori di convalida quando il codice è in conflitto con la progettazione. In presenza delle condizioni seguenti è possibile ad esempio che si verifichino errori di convalida:

- Un artefatto viene assegnato al livello errato. In questo caso, spostare l'elemento.

- Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.

Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. È possibile eseguire questa attività in modo iterativo.

Nella sezione seguente viene descritta la sintassi usata negli errori, viene illustrato il significato degli errori e vengono indicate le operazioni che è possibile eseguire per risolverli o gestirli.

|**Sintassi**|**Descrizione**|
|-|-|
|*Artefatto*(*tipoelementon*)|*Artefatto* è un artefatto associato a un livello nel diagramma delle dipendenze.<br /><br /> *Tipoelementon* è il tipo di *artefatto*, ad esempio una **classe** o un **Metodo**, ad esempio:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metodo)|
|*NamespaceNameN*|Nome di uno spazio dei nomi.|
|*LayerNameN*|Nome di un livello nel diagramma delle dipendenze.|
|*DependencyType*|Tipo di relazione di dipendenza tra *elemento1* e *Artifact2*. Ad esempio, *elemento1* ha una relazione **calls** con *Artifact2*.|

| **Sintassi di errore** | **Descrizione errore** |
|-|-|
| DV0001: **dipendenza non valida** | Questo problema viene segnalato quando un elemento di codice (spazio dei nomi, tipo, membro) mappato a un livello fa riferimento a un elemento di codice mappato a un altro livello, ma non esiste alcuna freccia di dipendenza tra questi livelli nel diagramma di convalida delle dipendenze che contiene questi livelli. Si tratta di una violazione del vincolo di dipendenza. |
| DV1001: **nome dello spazio dei nomi non valido** | Questo problema viene segnalato su un elemento di codice associato a un livello che la proprietà "Allowed namespace names" non contiene lo spazio dei nomi in cui è definito questo elemento di codice. Si tratta di una violazione di vincolo di denominazione. Si noti che la sintassi dei nomi degli spazi dei nomi consentiti è costituita da un elenco di spazi dei nomi con un punto e virgola in cui è consentito definire gli elementi di codice associati al livello. |
| DV1002: **dipendenza dallo spazio dei nomi non referenziabile** | Questo problema viene segnalato su un elemento di codice associato a un livello e fa riferimento a un altro elemento di codice definito in uno spazio dei nomi definito nella proprietà "spazio dei nomi non referenziabile" del livello. Si tratta di una violazione di vincolo di denominazione. Si noti che la proprietà "spazi dei nomi non referenziabili" è definita come un elenco separato da punti e virgola di spazi dei nomi a cui non è necessario fare riferimento negli elementi di codice associati a questo livello. |
| DV1003: **nome dello spazio dei nomi non consentito** | Questo problema viene segnalato su un elemento di codice associato a un livello che contiene lo spazio dei nomi in cui è definito questo elemento di codice. Si tratta di una violazione di vincolo di denominazione. Si noti che la proprietà "nome spazio dei nomi non consentito" è definita come un elenco di spazi dei nomi separati da punto e virgola in cui gli elementi di codice associati a questo livello non devono essere definiti. |
| DV3001: **collegamento mancante** | Il livello '*LayerName*' si collega a'*artefatto*' che non è stato trovato. Probabilmente manca un riferimento a un assembly. |
| DV9001: l' **analisi dell'architettura ha rilevato errori interni** | I risultati potrebbero non essere completi. Per altre informazioni, vedere il log dettagliato degli eventi di compilazione o la finestra di output. |

## <a name="see-also"></a>Vedere anche

- [Convalida delle dipendenze in tempo reale in Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)
- [Video: convalidare le dipendenze dell'architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
