---
title: Creare un set di regole di analisi del codice personalizzato
ms.date: 11/02/2018
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4659efef9b233284a593fecd5c8404cb2650b0c
ms.sourcegitcommit: 4d7c883ea3eedd795eeb4a9d3bd3dee82c8e093e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/26/2020
ms.locfileid: "88893268"
---
# <a name="customize-a-rule-set"></a>Personalizzare un set di regole

È possibile creare un set di regole personalizzato per soddisfare esigenze specifiche del progetto per l'analisi del codice.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>Creare un set di regole personalizzato da un set di regole esistente

Per creare un set di regole personalizzato, è possibile aprire un set di regole incorporato nell' **Editor del set di regole**. Da qui è possibile aggiungere o rimuovere regole specifiche ed è possibile modificare l'azione che si verifica quando viene violata una regola, &mdash; ad esempio, viene visualizzato un avviso o un errore.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.

2. Nelle pagine delle **Proprietà** selezionare la scheda **analisi codice** .

::: moniker range="vs-2017"

3. Nell'elenco a discesa **Esegui questo set di regole** effettuare una delle operazioni seguenti:

::: moniker-end

::: moniker range=">=vs-2019"

3. Nell'elenco a discesa **regole attive** effettuare una delle operazioni seguenti:

::: moniker-end

   - Scegliere il set di regole che si desidera personalizzare.

     \- - oppure -

   - Selezionare **\<Browse>** questa impostazione per specificare un set di regole esistente non presente nell'elenco.

4. Selezionare **Apri** per visualizzare le regole nell'Editor set di regole.

> [!NOTE]
> Se si dispone di un progetto .NET Core o .NET Standard, il processo è leggermente diverso perché non è disponibile alcuna scheda delle proprietà di **analisi del codice** . attenersi alla procedura per [copiare un set di regole predefinito nel progetto e impostarlo come set di regole attivo](analyzer-rule-sets.md). Dopo aver copiato su un set di regole, è possibile [modificarlo nell'editor del set di regole di Visual Studio](working-in-the-code-analysis-rule-set-editor.md) aprendolo dal **Esplora soluzioni**.

## <a name="create-a-new-rule-set"></a>Creare un nuovo set di regole

È possibile creare un nuovo file del set di regole dalla finestra di dialogo **nuovo file** :

1. Selezionare **file**  >  **nuovo**  >  **file**oppure premere **CTRL** + **N**.

2. Nella finestra di dialogo **nuovo file** selezionare la categoria **generale** a sinistra e quindi selezionare **set di regole di analisi codice**.

3. Seleziona **Apri**.

   Il nuovo file con *estensione ruleset* verrà aperto nell'Editor set di regole.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Creare un set di regole personalizzato da più set di regole

> [!NOTE]
> La seguente procedura non si applica ai progetti .NET Core, che non dispongono di una scheda delle proprietà di **analisi del codice** .

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.

2. Nelle pagine delle **Proprietà** selezionare la scheda **analisi codice** .

::: moniker range="vs-2017"

3. Selezionare **\<Choose multiple rule sets>** da **Esegui questo set di regole**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Selezionare **\<Choose multiple rule sets>** da **regole attive**.

::: moniker-end

4. Nella finestra di dialogo **Aggiungi o Rimuovi set di regole** scegliere i set di regole che si desidera includere nel nuovo set di regole.

   ![Finestra di dialogo Aggiungi o Rimuovi set di regole](media/add-remove-rule-sets.png)

5. Selezionare **Salva con**nome, immettere un nome per il file con *estensione ruleset* , quindi selezionare **Salva**.

   Il nuovo set di regole è selezionato nell'elenco **Esegui questo set di regole** .

6. Selezionare **Apri** per aprire il nuovo set di regole nell'Editor set di regole.

## <a name="rule-precedence"></a>Precedenza delle regole

- Se la stessa regola è elencata due o più volte in un set di regole con diversi livelli di gravità, il compilatore genera un errore. Ad esempio:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Se la stessa regola è elencata due o più volte in un set di regole con lo *stesso* livello di gravità, è possibile che venga visualizzato il seguente avviso nel **Elenco errori**:

   **CA0063: non è stato possibile caricare il file \[ del set di regole ' your]. RuleSet ' o uno dei file del set di regole dipendenti. Il file non è conforme allo schema del set di regole.**

- Se il set di regole include un set di regole figlio utilizzando un tag di **inclusione** e i set di regole figlio e padre entrambi elencano la stessa regola ma con livelli di gravità diversi, la gravità nel set di regole padre avrà la precedenza. Ad esempio:

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>Nome e descrizione

Per modificare il nome visualizzato di un set di regole aperto nell'editor, aprire la finestra **Proprietà** selezionando **Visualizza**  >  **finestra Proprietà** sulla barra dei menu. Immettere il nome visualizzato nella casella **nome** . È anche possibile immettere una descrizione per il set di regole.

## <a name="next-steps"></a>Passaggi successivi

Ora che si dispone di un set di regole, il passaggio successivo consiste nel personalizzare le regole aggiungendo o rimuovendo regole o modificando la gravità delle violazioni delle regole.

> [!div class="nextstepaction"]
> [Modificare le regole nell'Editor set di regole](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Vedere anche

- [Procedura: Configurare l'analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)
