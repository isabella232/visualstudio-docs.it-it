---
title: Criteri di archiviazione dell'analisi codice personalizzati per codice gestito
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b9eec66ec24c30b6e0df835d16805ea00eb08ac2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371768"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementare i criteri di archiviazione di analisi codice personalizzati per il codice gestito

Un criterio di archiviazione dell'analisi del codice specifica un set di regole che i membri di un progetto Azure DevOps devono eseguire sul codice sorgente prima di archiviarlo nel controllo della versione. Microsoft fornisce un set di *set* di regole standard che raggruppano le regole di analisi del codice in aree funzionali. I set di regole dei *criteri di archiviazione personalizzati* specificano un set di regole di analisi del codice specifiche di un progetto. Un set di regole viene archiviato in un file con estensione RuleSet.

I criteri di archiviazione vengono impostati a livello di progetto Azure DevOps e specificati dal percorso di un file con estensione ruleset nell'albero del controllo della versione. Non esistono restrizioni per il percorso del controllo della versione del set di regole personalizzate dei criteri team.

L'analisi del codice viene configurata per i singoli progetti di codice nella finestra proprietà per ogni progetto. Un set di regole personalizzato per un progetto di codice viene specificato dalla posizione fisica del file con estensione RuleSet nel computer locale. Quando si specifica un file con estensione RuleSet che si trova nella stessa unità del progetto di codice, Visual Studio usa un percorso relativo del file nella configurazione del progetto.

Una procedura consigliata per la creazione di un set di regole personalizzate del progetto DevOps di Azure consiste nell'archiviare il file con estensione ruleset dei criteri di archiviazione in una cartella speciale che non fa parte di alcun progetto di codice. Se si archivia il file in una cartella dedicata, è possibile applicare le autorizzazioni che limitano gli utenti che possono modificare il file della regola ed è possibile spostare facilmente la struttura di directory che contiene il progetto in un'altra directory o computer.

## <a name="create-the-project-custom-check-in-rule-set"></a>Creare il set di regole di archiviazione personalizzate del progetto

Per creare un set di regole personalizzato per un progetto DevOps di Azure, creare innanzitutto una cartella speciale per il set di regole dei criteri di archiviazione in **Esplora controllo codice sorgente**. Si crea quindi il file del set di regole e si aggiunge il file al controllo della versione. Infine, specificare il set di regole come criterio di archiviazione dell'analisi del codice per il progetto.

> [!NOTE]
> Per creare una cartella in un progetto DevOps di Azure, è innanzitutto necessario eseguire il mapping della radice del progetto a un percorso nel computer locale.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Per creare la cartella del controllo della versione per il set di regole dei criteri di archiviazione

1. In Team Explorer espandere il nodo del progetto, quindi fare clic su **controllo del codice sorgente**.

2. Nel riquadro **cartelle** , fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **nuova cartella**.

3. Nel riquadro principale del controllo del codice sorgente fare clic con il pulsante destro del mouse su **nuova cartella**, scegliere **Rinomina**e digitare un nome per la cartella del set di regole.

### <a name="to-create-the-check-in-policy-rule-set"></a>Per creare il set di regole dei criteri di archiviazione

1. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **File**.

2. Nell'elenco **categorie** fare clic su **generale**.

3. Nell'elenco **modelli** fare doppio clic su **set di regole di analisi del codice**.

4. [Specificare le regole](../code-quality/how-to-create-a-custom-rule-set.md) da includere nel set di regole, quindi salvare il file del set di regole nella cartella del set di regole creata.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Per aggiungere il file del set di regole al controllo della versione

1. In **Esplora controllo codice sorgente**fare clic con il pulsante destro del mouse sulla nuova cartella e quindi scegliere **Aggiungi elementi alla cartella**.

     Per ulteriori informazioni, vedere [git e Azure Repos](/azure/devops/repos/git/overview?view=vsts).

2. Fare clic sul file del set di regole creato, quindi fare clic su **fine**.

     Il file viene aggiunto al controllo del codice sorgente ed è stato estratto.

3. Nella finestra Dettagli **Esplora controllo codice sorgente** fare clic con il pulsante destro del mouse sul nome del file e quindi scegliere **Archivia modifiche in sospeso**.

4. Nella finestra di dialogo **Archivia** è possibile aggiungere un commento, quindi fare clic su **Archivia**.

    > [!NOTE]
    > Se sono già stati configurati criteri di archiviazione dell'analisi del codice per il progetto Azure DevOps ed è stata selezionata l'opzione **applica archiviazione per contenere solo file che fanno parte della soluzione corrente**, verrà generato un avviso di errore dei criteri. Nella finestra di dialogo errore criteri selezionare **Sostituisci errore criteri e continua archiviazione**. Aggiungere un commento obbligatorio, quindi fare clic su **OK**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Per specificare il file del set di regole come criterio di archiviazione

1. Scegliere **Impostazioni progetto**dal menu **Team** , quindi fare clic su controllo del **codice sorgente**.

2. Fare clic su **criteri di archiviazione**e quindi su **Aggiungi**.

3. Nell'elenco dei **criteri di archiviazione** fare doppio clic su **analisi codice**e verificare che la casella di controllo **Imponi analisi codice per codice gestito** sia selezionata.

4. Nell'elenco **Esegui questo set di regole** fare clic su **\<Select Rule Set from Source Control>** .

5. Digitare il percorso del file del set di regole dei criteri di archiviazione nel controllo della versione.

     Il percorso deve essere conforme alla sintassi seguente:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > È possibile copiare il percorso usando una delle procedure seguenti in **Esplora controllo codice sorgente**:

    - Nel riquadro **cartelle** fare clic sulla cartella che contiene il file del set di regole. Copiare il percorso del controllo della versione della cartella che viene visualizzato nella casella **origine** e digitare manualmente il nome del file del set di regole.

    - Nella finestra dei dettagli fare clic con il pulsante destro del mouse sul file del set di regole e quindi scegliere **Proprietà**. Nella scheda **generale** copiare il valore in **nome server**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Sincronizzare i progetti di codice con il set di regole dei criteri di archiviazione

È possibile specificare un set di regole dei criteri di archiviazione del progetto come set di regole di analisi del codice di una configurazione del progetto di codice nella finestra di dialogo Proprietà del progetto di codice. Se il set di regole si trova nella stessa unità del progetto di codice, viene usato un percorso relativo per specificare il set di regole quando il percorso è selezionato nella finestra di dialogo file. Il percorso relativo consente alle impostazioni delle proprietà del progetto di essere portabili in altri computer che utilizzano strutture di controllo della versione locali simili.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Per specificare un set di regole di progetto come set di regole di un progetto di codice

1. Se necessario, recuperare la cartella del set di regole dei criteri di archiviazione e il file dal controllo della versione.

   È possibile eseguire questo passaggio in **Esplora controllo codice sorgente** facendo clic con il pulsante destro del mouse sulla cartella del set di regole e quindi scegliendo **ottenere la versione più recente**.

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto di codice, quindi scegliere **Proprietà**.

3. **Fare clic su analisi codice**.

4. Se necessario, fare clic sulle opzioni appropriate negli elenchi **configurazione** e **piattaforma** .

::: moniker range="vs-2017"

5. Per eseguire l'analisi del codice ogni volta che il progetto di codice viene compilato usando la configurazione specificata, selezionare **Abilita analisi codice durante la compilazione**.

::: moniker-end

::: moniker range=">=vs-2019"

5. Per eseguire l'analisi del codice ogni volta che il progetto di codice viene compilato usando la configurazione specificata, selezionare **Esegui in compilazione** nella sezione **analizzatori binari** .

::: moniker-end

6. Nell'elenco **Esegui questo set di regole** fare clic su **\<Browse>** .

8. Consente di selezionare la versione locale del file del set di regole dei criteri di archiviazione.
