---
title: Configurare l'analisi del codice
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f1bfa8c6e5260fb4afd20b882e2bdfc718647f4b
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448974"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Procedura: configurare l'analisi legacy per il codice gestito

In Visual Studio è possibile scegliere da un elenco di [set di regole](../code-quality/rule-set-reference.md) di analisi codice da applicare a un progetto di codice gestito. Per impostazione predefinita, è selezionato il set di regole **minime consigliate Microsoft** , ma è possibile applicare un set di regole diverso se lo si desidera. I set di regole possono essere applicati a uno o più progetti in una soluzione.

> [!NOTE]
> Questo articolo si applica all'analisi legacy e non agli [analizzatori di codice basati su .NET Compiler Platform](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurare un set di regole per un progetto di .NET Framework

1. Aprire la scheda **analisi codice** nelle pagine delle proprietà del progetto. Questa operazione può essere eseguita in uno dei modi seguenti:

   - In **Esplora soluzioni**selezionare il progetto. Nella barra dei menu selezionare **analizza** > **configura analisi codice** > **per \<projectname >** .

   - Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** , scegliere **Proprietà**, quindi selezionare la scheda **analisi codice** .

2. Negli elenchi **configurazione** e **piattaforma** Selezionare la configurazione di compilazione e la piattaforma di destinazione.

::: moniker range="vs-2017"

3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato usando la configurazione selezionata, selezionare **Abilita analisi codice durante la compilazione**. È anche possibile eseguire manualmente l'analisi del codice selezionando **analizza** > **eseguire analisi**del codice  > **eseguire l'analisi del codice su \<projectname >** .

::: moniker-end

::: moniker range=">=vs-2019"

3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato usando la configurazione selezionata, selezionare **Esegui in compilazione** nella sezione **analizzatori binari** . È anche possibile eseguire manualmente l'analisi del codice selezionando **analizza** > **eseguire analisi**del codice  > **eseguire l'analisi del codice su \<projectname >** .

::: moniker-end

4. Per visualizzare gli avvisi dal codice generato, deselezionare la casella di controllo non **visualizzare i risultati del codice generato** .

    > [!NOTE]
    > Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello e non verrà sovrascritto.

::: moniker range="vs-2017"

5. Nell'elenco **Esegui questo set di regole** effettuare una delle operazioni seguenti:

::: moniker-end

::: moniker range=">=vs-2019"

5. Nell'elenco **regole attive** effettuare una delle operazioni seguenti:

::: moniker-end

    - Selezionare il set di regole che si desidera utilizzare.

    - Selezionare **\<Browse >** per trovare un set di regole personalizzato esistente non presente nell'elenco.

    - Definire un [set di regole personalizzato](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Specificare i set di regole per più progetti in una soluzione

Per impostazione predefinita, a tutti i progetti gestiti di una soluzione viene assegnato il set di regole di analisi del codice per le *regole minime consigliate di Microsoft* . È possibile modificare i set di regole assegnati ai progetti di una soluzione nella finestra di dialogo **Proprietà** per la soluzione.

1. Aprire la soluzione in Visual Studio.

2. Nel menu **analizza** selezionare **Configura analisi codice per la soluzione**.

3. Se necessario, espandere **Proprietà comuni**, quindi selezionare **Impostazioni analisi codice**.

4. È possibile specificare un set di regole per uno o più progetti:

    - Per specificare un set di regole per un singolo progetto, selezionare il nome del progetto.

    - Per specificare un set di regole per più progetti, tenere premuto **CTRL** e selezionare i nomi del progetto.

    - Per specificare tutti i progetti nella soluzione, tenere premuto **MAIUSC** e fare clic nell'elenco progetto.

5. Selezionare il campo **set di regole** di un progetto, quindi selezionare il nome del set di regole che si desidera applicare.

## <a name="see-also"></a>Vedere anche

- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)
