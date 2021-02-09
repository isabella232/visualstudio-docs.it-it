---
title: Configurare l'analisi del codice
ms.date: 04/04/2018
description: Informazioni su come configurare il set di regole usato dall'analisi del codice legacy di Visual Studio. Vedere come applicare un set di regole a uno o più progetti in una soluzione.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
- vs.codeanalysis.propertypages.asp
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8b76678b1e5c0f53502e24f8baee87ede3bd3ef6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860178"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Procedura: configurare l'analisi legacy per il codice gestito

In Visual Studio è possibile scegliere da un elenco di [set di regole](../code-quality/rule-set-reference.md) di analisi codice da applicare a un progetto di codice gestito. Per impostazione predefinita, è selezionato il set di regole **minime consigliate Microsoft** , ma è possibile applicare un set di regole diverso se lo si desidera. I set di regole possono essere applicati a uno o più progetti in una soluzione.

> [!NOTE]
> Questo articolo si applica all'analisi legacy e non agli [analizzatori di codice basati su .NET Compiler Platform](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurare un set di regole per un progetto di .NET Framework

1. Aprire la scheda **analisi codice** nelle pagine delle proprietà del progetto. È possibile precedere in uno dei modi seguenti:

   - In **Esplora soluzioni** scegliere il progetto. Sulla barra dei menu selezionare **analizza**  >  **Configura analisi codice**  >  **per \<projectname>**.

   - Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** , scegliere **Proprietà**, quindi selezionare la scheda **analisi codice** .

2. Negli elenchi **configurazione** e **piattaforma** scegliere la configurazione di compilazione e la piattaforma di destinazione.

::: moniker range="vs-2017"

3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato usando la configurazione selezionata, selezionare **Abilita analisi codice durante la compilazione**. È anche possibile eseguire manualmente l'analisi del codice selezionando **analizza**  >  **Esegui analisi codice**  >  **Esegui analisi \<projectname> del codice su**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato usando la configurazione selezionata, selezionare **Esegui in compilazione** nella sezione **analizzatori binari** . È anche possibile eseguire manualmente l'analisi del codice legacy. per ulteriori informazioni, vedere [procedura: eseguire manualmente l'analisi del codice legacy per il codice gestito](how-to-run-legacy-code-analysis-manually-for-managed-code.md) .

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

   - Selezionare **\<Browse>** questa impostazione per trovare un set di regole personalizzato esistente non presente nell'elenco.

   - Definire un [set di regole personalizzato](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Specificare i set di regole per più progetti in una soluzione

Per impostazione predefinita, a tutti i progetti gestiti di una soluzione viene assegnato il set di regole di analisi del codice per le *regole minime consigliate di Microsoft* . È possibile modificare i set di regole assegnati ai progetti di una soluzione nella finestra di dialogo **Proprietà** per la soluzione.

1. Aprire la soluzione in Visual Studio.

2. Nel menu **analizza** selezionare **Configura analisi codice per la soluzione**.

3. Se necessario, espandere **Proprietà comuni**, quindi selezionare **Impostazioni analisi codice**.

4. È possibile specificare un set di regole per uno o più progetti:

    - Per specificare un set di regole per un singolo progetto, scegliere il nome del progetto.

    - Per specificare un set di regole per più progetti, selezionare **CTRL** e i nomi del progetto.

    - Per specificare tutti i progetti nella soluzione, selezionare **MAIUSC** e l'elenco progetto.

5. Selezionare il campo **set di regole** di un progetto, quindi selezionare il nome del set di regole che si desidera applicare.

## <a name="see-also"></a>Vedi anche

- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)
