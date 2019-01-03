---
title: Creare un set di regole di analisi di codice personalizzato
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2a0b2de9450fc2e9350371b08f4a3a9bf8d9c1b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53929921"
---
# <a name="customize-a-rule-set"></a>Personalizzare un set di regole

È possibile creare una regola personalizzata impostata per soddisfare specifiche esigenze del progetto per l'analisi codice.

## <a name="create-a-custom-rule-set"></a>Creare un set di regole personalizzato

Per creare una regola personalizzata set, è possibile aprire una set di regole predefinite di **editor set di regole**. Da qui, è possibile aggiungere o rimuovere le regole specifiche ed è possibile modificare l'azione che si verifica quando una regola viene violata&mdash;, ad esempio, Mostra un avviso o un errore.

1. Nelle **Esplora soluzioni**, fare clic sul progetto e quindi selezionare **proprietà**.

2. Nel **delle proprietà** pagine, selezionare la **analisi del codice** scheda.

3. Nel **eseguire questo set di regole** riepilogo, effettuare una delle operazioni seguenti:

   - Selezionare il set di regole che si desidera personalizzare.

     \- oppure -

   - Selezionare  **\<Sfoglia >** per specificare set di una regola esistente non incluso nell'elenco.

4. Selezionare **aperto** per visualizzare le regole nell'editor set di regole.

È anche possibile creare un nuovo file di set di regole dal **nuovo File** finestra di dialogo:

1. Selezionare **File** > **New** > **File**, o premere **Ctrl**+**N**.

2. Nel **nuovo File** finestra di dialogo, seleziona il **generali** categoria a sinistra e quindi selezionare **Set di regole di analisi codice**.

3. Selezionare **Apri**.

   Il nuovo *ruleSet* file verrà aperto nell'editor set di regole.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Creare una regola personalizzata impostata da più set di regole

1. In Esplora soluzioni fare clic sul progetto e quindi selezionare **proprietà**.

2. Nel **delle proprietà** pagine, selezionare la **analisi del codice** scheda.

3. Selezionare  **\<Scegli più set di regole... >** dalla **eseguire questo set di regole**.

4. Nel **Aggiungi o Rimuovi set di regole** nella finestra di dialogo selezionare i set di regole si desidera includere nel nuovo set di regole.

   ![Aggiungere o rimuovere la finestra di dialogo set di regole](media/add-remove-rule-sets.png)

5. Selezionare **Salva con nome**, immettere un nome per il *ruleSet* e quindi selezionare **Salva**.

   Il nuovo set di regole è selezionato nel **eseguire questo set di regole** elenco.

6. Selezionare **aprire** per aprire il nuovo set di regole in editor set di regole.

### <a name="rule-precedence"></a>Precedenza delle regole

- Se la stessa regola è elencata due o più volte in una set di regole con diversi livelli di gravità, il compilatore genera un errore. Ad esempio:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Se la stessa regola è elencata due o più volte in una set di regole con il *stessi* gravità, si può vedere il seguente avviso nella **elenco errori**:

   **CA0063: Impossibile caricare il file del set di regole '\[il] estensione ruleset ' o impostare una delle relative regole dipendenti file. Il file non è conforme allo schema del set di regole.**

- Se il set di regole include una regola figlio impostata in un' **inclusione** tag e i set di regole padre e figlio entrambi elencare la stessa regola ma con gravità diversa, quindi il livello di gravità nel set di regole padre ha la precedenza. Ad esempio:

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

Per modificare il nome visualizzato di un set di regole che viene aperto nell'editor, aprire il **delle proprietà** finestra selezionando **View** > **finestra proprietà** nella barra dei menu. Immettere il nome visualizzato nei **nome** casella. È anche possibile immettere una descrizione per il set di regole.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver creato una regola impostata, il passaggio successivo consiste nel personalizzare le regole aggiungendo o rimuovendo le regole o modificando il livello di gravità di violazioni delle regole.

> [!div class="nextstepaction"]
> [Modificare le regole nell'editor set di regole](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Vedere anche

- [Procedura: Configura analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)