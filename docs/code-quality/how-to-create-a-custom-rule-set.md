---
title: Creare un set di regole di analisi del codice personalizzato
ms.date: 11/02/2018
description: Informazioni su come personalizzare i set di regole di analisi del codice in Visual Studio. Informazioni su come creare nuovi set da zero o da set esistenti. Informazioni sulla precedenza delle regole.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 181f94ccc9b83053673e49746d757708afdbf966
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139613"
---
# <a name="customize-a-rule-set"></a>Personalizzare un set di regole

È possibile creare un set di regole personalizzato per soddisfare esigenze specifiche del progetto per l'analisi del codice.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>Creare un set di regole personalizzato da un set di regole esistente

Per creare un set di regole personalizzato, è possibile aprire un set di regole predefinito **nell'editor del set di regole**. Da qui è possibile aggiungere o rimuovere regole specifiche ed è possibile modificare l'azione che si verifica quando viene violata una regola, ad esempio visualizzare un avviso &mdash; o un errore.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e quindi **scegliere Proprietà.**

2. Nella pagina **Proprietà** selezionare la scheda **Code Analysis** proprietà.

::: moniker range="vs-2017"

3. **Nell'elenco a discesa Run this rule set** (Esegui questo set di regole) eseguire una delle operazioni seguenti:

::: moniker-end

::: moniker range=">=vs-2019"

3. **Nell'elenco a** discesa Regole attive eseguire una delle operazioni seguenti:

::: moniker-end

   - Scegliere il set di regole da personalizzare.

     \- - oppure -

   - Selezionare **\<Browse>** questa opzione per specificare un set di regole esistente non in elenco.

4. Selezionare **Apri** per visualizzare le regole nell'editor del set di regole.

> [!NOTE]
> Se si ha un progetto .NET Core o .NET Standard, il processo è leggermente diverso perché la scheda **Code Analysis** nelle proprietà del progetto non supporta le stesse opzioni. Seguire i passaggi per copiare un set di regole [predefinito nel progetto e impostarlo come set di regole attivo.](/dotnet/fundamentals/code-analysis/code-quality-rule-options) Dopo aver copiato un set di regole, è possibile modificarlo [nell'editor](working-in-the-code-analysis-rule-set-editor.md) Visual Studio set di regole aprendolo **da Esplora soluzioni**.

## <a name="create-a-new-rule-set"></a>Creare un nuovo set di regole

È possibile creare un nuovo file del set di regole dalla **finestra di dialogo Nuovo file:**

1. Selezionare **File**  >  **Nuovo**  >  **file** o premere **CTRL** + **N.**

2. Nella finestra **di dialogo** Nuovo file selezionare la **categoria Generale** a sinistra e quindi selezionare Code Analysis set **di regole.**

3. Selezionare **Open** (Apri).

   Il nuovo file *con estensione ruleset* viene aperto nell'editor del set di regole.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Creare un set di regole personalizzato da più set di regole

> [!NOTE]
> La procedura seguente non si applica ai progetti .NET Core o .NET Standard, che non supportano le stesse funzionalità nella scheda Code Analysis **proprietà.**

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e quindi **scegliere Proprietà.**

2. Nella pagina **Proprietà** selezionare la scheda **Code Analysis** proprietà.

::: moniker range="vs-2017"

3. Selezionare **\<Choose multiple rule sets>** da Esegui questo set di **regole**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Selezionare **\<Choose multiple rule sets>** da **Regole attive.**

::: moniker-end

4. Nella finestra **di dialogo Aggiungi o** rimuovi set di regole scegliere i set di regole da includere nel nuovo set di regole.

   ![Finestra di dialogo Aggiungi o rimuovi set di regole](media/add-remove-rule-sets.png)

5. Selezionare **Salva con nome,** immettere un nome per il file con estensione *ruleset* e quindi selezionare **Salva.**

   Il nuovo set di regole viene selezionato **nell'elenco Esegui questo set di** regole .

6. Selezionare **Apri** per aprire il nuovo set di regole nell'editor del set di regole.

## <a name="rule-precedence"></a>Precedenza delle regole

- Se la stessa regola è elencata due o più volte in un set di regole con livelli di gravità diversi, il compilatore genera un errore. Esempio:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Se la stessa regola è elencata due o  più volte in un set di regole con lo stesso livello di gravità, è possibile che nell'Elenco errori venga visualizzato **l'avviso seguente:**

   **CA0063: Non è stato possibile caricare il file del set di regole \[ 'your].ruleset' o uno dei file del set di regole dipendenti. Il file non è conforme allo schema del set di regole.**

- Se il set di regole include un set di regole figlio usando un tag **Include** e la regola figlio e la regola padre elencano entrambi la stessa regola ma con livelli di gravità diversi, la gravità nel set di regole padre ha la precedenza. Esempio:

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

Per modificare il nome visualizzato di un set di regole  aperto nell'editor, aprire la finestra Proprietà selezionando Visualizza finestra Proprietà   >   sulla barra dei menu. Immettere il nome visualizzato nella **casella** Nome . È anche possibile immettere una descrizione per il set di regole.

## <a name="next-steps"></a>Passaggi successivi

Ora che è disponibile un set di regole, il passaggio successivo consiste nel personalizzare le regole aggiungendo o rimuovendo regole o modificando la gravità delle violazioni delle regole.

> [!div class="nextstepaction"]
> [Modificare le regole nell'editor del set di regole](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Vedi anche

- [Procedura: Configurare l'analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)