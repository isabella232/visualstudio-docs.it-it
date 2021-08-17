---
title: Criteri di archiviazione dell'analisi codice personalizzati per il codice gestito
ms.date: 11/04/2016
description: Informazioni su come creare criteri di archiviazione personalizzati per l'analisi del codice. Informazioni su come assicurarsi che Visual Studio codice gestito sia conforme ai criteri Azure DevOps progetto.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: d460c6f8e683254d8d7e709d1ab2eedb3dbc144acd12a7f25839b1ae562fca40
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455309"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementare i criteri di archiviazione di analisi codice personalizzati per il codice gestito

I criteri di archiviazione dell'analisi del codice specificano un set di regole che i membri di un progetto Azure DevOps devono eseguire nel codice sorgente prima di essere archiviati nel controllo della versione. Microsoft fornisce un set di set di regole standard *che raggruppano* le regole di analisi del codice in aree funzionali. *I set di regole dei criteri di archiviazione* personalizzati specificano un set di regole di analisi del codice specifiche di un progetto. Un set di regole viene archiviato in un file con estensione ruleset.

I criteri di archiviazione vengono impostati a Azure DevOps progetto e specificati dal percorso di un file con estensione ruleset nell'albero del controllo della versione. Non sono presenti restrizioni sulla posizione del controllo della versione del set di regole personalizzate dei criteri del team.

L'analisi del codice è configurata per i singoli progetti di codice nella finestra delle proprietà per ogni progetto. Un set di regole personalizzato per un progetto di codice viene specificato dal percorso fisico del file con estensione ruleset nel computer locale. Quando viene specificato un file con estensione ruleset che si trova nella stessa unità del progetto di codice, Visual Studio usa un percorso relativo al file nella configurazione del progetto.

Una procedura consigliata per la creazione di un set di regole personalizzate del progetto Azure DevOps consiste nell'archiviare il file con estensione ruleset dei criteri di archiviazione in una cartella speciale che non fa parte di alcun progetto di codice. Se si archivia il file in una cartella dedicata, è possibile applicare autorizzazioni che limitano chi può modificare il file delle regole ed è possibile spostare facilmente la struttura di directory che contiene il progetto in un'altra directory o computer.

## <a name="create-the-project-custom-check-in-rule-set"></a>Creare il Project set di regole di archiviazione personalizzato

Per creare un set di regole personalizzato per un progetto Azure DevOps, creare prima di tutto una cartella speciale per il set di regole dei criteri di archiviazione in **Esplora controllo codice sorgente**. Creare quindi il file del set di regole e aggiungerlo al controllo della versione. Infine, si specifica il set di regole come criteri di archiviazione dell'analisi del codice per il progetto.

> [!NOTE]
> Per creare una cartella in un Azure DevOps, è prima necessario eseguire il mapping della radice del progetto a un percorso nel computer locale.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Per creare la cartella del controllo della versione per il set di regole dei criteri di archiviazione

1. In Team Explorer espandere il nodo del progetto e quindi fare clic su **Controllo del codice sorgente**.

2. Nel riquadro **Cartelle** fare clic con il pulsante destro del mouse sul progetto e quindi scegliere **Nuova cartella**.

3. Nel riquadro principale del controllo del codice sorgente fare clic con il pulsante destro del mouse su **Nuova cartella,** scegliere **Rinomina** e digitare un nome per la cartella del set di regole.

### <a name="to-create-the-check-in-policy-rule-set"></a>Per creare il set di regole dei criteri di archiviazione

1. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **File**.

2. **Nell'elenco Categorie** fare clic su **Generale**.

3. **Nell'elenco Modelli** fare doppio clic su Code Analysis **set di regole**.

4. [Specificare le regole](../code-quality/how-to-create-a-custom-rule-set.md) da includere nel set di regole e quindi salvare il file del set di regole nella cartella del set di regole creata.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Per aggiungere il file del set di regole al controllo della versione

1. In **Esplora controllo codice sorgente** fare clic con il pulsante destro del mouse sulla nuova cartella e quindi scegliere **Aggiungi elementi alla cartella**.

     Per altre informazioni, vedere [Git e Azure Repos](/azure/devops/repos/git/overview?view=vsts&preserve-view=true).

2. Fare clic sul file del set di regole creato e quindi fare clic su **Fine**.

     Il file viene aggiunto al controllo del codice sorgente ed estratto dall'utente.

3. Nella finestra **Esplora controllo codice sorgente** dettagli fare clic con il pulsante destro del mouse sul nome del file e quindi scegliere **Archivia modifiche in sospeso**.

4. Nella finestra **di dialogo Archivia** è possibile aggiungere un commento e quindi fare clic su **Archivia**.

    > [!NOTE]
    > Se sono già stati configurati criteri di archiviazione dell'analisi codice per il progetto Azure DevOps ed è stata selezionata l'opzione Imponi archiviazione per contenere solo i file che fanno parte della soluzione **corrente,** verrà attivato un avviso di errore dei criteri. Nella finestra di dialogo Policy Failure (Errore criteri) selezionare **Override policy failure (Override policy failure) (Override policy failure and continue checkin ).** Aggiungere un commento obbligatorio e quindi fare clic su **OK.**

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Per specificare il file del set di regole come criteri di archiviazione

1. Scegliere Controllo **del** codice **sorgente dal** menu Team Project Impostazioni e quindi fare clic su Controllo del codice **sorgente**.

2. Fare **clic su Criteri di archiviazione** e quindi su **Aggiungi**.

3. **Nell'elenco Criteri** di archiviazione fare doppio clic su **Code Analysis** e verificare che la casella di controllo **Imponi** Code Analysis per codice gestito sia selezionata.

4. **Nell'elenco Esegui questo set di regole** fare clic su **\<Select Rule Set from Source Control>** .

5. Digitare il percorso del file del set di regole dei criteri di archiviazione nel controllo della versione.

     Il percorso deve essere conforme alla sintassi seguente:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > È possibile copiare il percorso usando una delle procedure seguenti in **Esplora controllo codice sorgente**:

    - Nel riquadro **Cartelle** fare clic sulla cartella che contiene il file del set di regole. Copiare il percorso del controllo della versione della cartella visualizzata nella casella **Origine** e digitare manualmente il nome del file del set di regole.

    - Nella finestra dei dettagli fare clic con il pulsante destro del mouse sul file del set di regole e quindi scegliere **Proprietà**. Nella scheda **Generale** copiare il valore in **Nome server**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Sincronizzare i progetti di codice con il set di regole dei criteri di archiviazione

Specificare un set di regole dei criteri di archiviazione del progetto come set di regole di analisi del codice di una configurazione del progetto di codice nella finestra di dialogo delle proprietà del progetto di codice. Se il set di regole si trova nella stessa unità del progetto di codice, viene usato un percorso relativo per specificare il set di regole quando il percorso viene selezionato dalla finestra di dialogo file. Il percorso relativo consente alle impostazioni delle proprietà del progetto di essere portabili ad altri computer che usano strutture di controllo della versione locali simili.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Per specificare un set di regole di progetto come set di regole di un progetto di codice

1. Se necessario, recuperare la cartella e il file del set di regole dei criteri di archiviazione dal controllo della versione.

   È possibile eseguire questo passaggio **in** Esplora controllo codice sorgente facendo clic con il pulsante destro del mouse sulla cartella del set di regole e quindi scegliendo Ottieni **ultima versione**.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di codice e quindi scegliere **Proprietà**.

3. **Fare clic Code Analysis**.

4. Se necessario, fare clic sull'opzione appropriata negli **elenchi Configurazione** **e** Piattaforma.

::: moniker range="vs-2017"

5. Per eseguire l'analisi del codice ogni volta che il progetto di codice viene compilato usando la configurazione specificata, selezionare Abilita Code Analysis **alla compilazione**.

::: moniker-end

::: moniker range=">=vs-2019"

5. Per eseguire l'analisi del codice ogni volta che il progetto di codice viene compilato usando la configurazione specificata, selezionare Esegui alla **compilazione** nella **sezione Analizzatori binari.**

::: moniker-end

6. **Nell'elenco Esegui questo set di regole** fare clic su **\<Browse>** .

8. Selezionare la versione locale del file del set di regole dei criteri di archiviazione.
