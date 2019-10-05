---
title: Configura analisi codice
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
ms.openlocfilehash: 86aa308369ef93792126c7f8da5f59f94ef0c02a
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975107"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Procedura: Configurare l'analisi legacy per il codice gestito

In Visual Studio è possibile scegliere da un elenco di [set di regole](../code-quality/rule-set-reference.md) di analisi codice da applicare a un progetto di codice gestito. Per impostazione predefinita, il **Microsoft regole minime** set di regole è selezionato, ma è possibile applicare una regola diversa se si desidera impostare. Set di regole possono essere applicati a uno o più progetti in una soluzione.

> [!NOTE]
> Questo articolo si applica all'analisi legacy e non agli [analizzatori di codice basati su .NET Compiler Platform](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurare un set di regole per un progetto di .NET Framework

1. Aprire il **analisi del codice** scheda nelle pagine delle proprietà del progetto. È possibile eseguire questa operazione in uno dei modi seguenti:

   - Nelle **Esplora soluzioni**, selezionare il progetto. Nella barra dei menu, selezionare **Analyze** > **Configura analisi codice** > **per \<NomeProgetto >** .

   - Fare clic sul progetto in **Esplora soluzioni** e selezionare **delle proprietà**e quindi selezionare il **analisi del codice** scheda.

2. Nel **Configuration** e **piattaforma** elenchi, selezionare la piattaforma di destinazione e configurazione di compilazione.

::: moniker range="vs-2017"

3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato usando la configurazione selezionata, selezionare **Abilita analisi codice durante la compilazione**. È anche possibile eseguire manualmente l'analisi del codice selezionando **Analyze** > **Esegui analisi del codice** > **Esegui analisi del codice \<NomeProgetto >** .

::: moniker-end

::: moniker range=">=vs-2019"

3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato usando la configurazione selezionata, selezionare **Esegui in compilazione** nella sezione **analizzatori binari** . È anche possibile eseguire manualmente l'analisi del codice selezionando **Analyze** > **Esegui analisi del codice** > **Esegui analisi del codice \<NomeProgetto >** .

::: moniker-end

4. Per visualizzare gli avvisi del codice generato, deselezionare il **non visualizzare i risultati dal codice generato** casella di controllo.

    > [!NOTE]
    > Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello e non verrà sovrascritto.

::: moniker range="vs-2017"

5. Nel **eseguire questo set di regole** elenco, effettuare una delle operazioni seguenti:

::: moniker-end

::: moniker range=">=vs-2019"

5. Nell'elenco **regole attive** effettuare una delle operazioni seguenti:

::: moniker-end

    - Selezionare il set di regole che si desidera utilizzare.

    - Selezionare **\<Browse >** per trovare un set di regole personalizzato esistente non presente nell'elenco.

    - Definire un [set di regole personalizzate](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Specificare il set di regole per più progetti in una soluzione

Per impostazione predefinita, tutti i progetti gestiti di una soluzione vengono assegnati i *Microsoft regole minime* set di regole di analisi del codice. È possibile modificare i set di regole che vengono assegnati ai progetti di una soluzione nel **proprietà** finestra di dialogo per la soluzione.

1. Aprire la soluzione in Visual Studio.

2. Nel **Analyze** dal menu **Configura analisi codice per la soluzione**.

3. Se necessario, espandere **proprietà comuni**, quindi selezionare **impostazioni di analisi codice**.

4. È possibile specificare una set di regole per uno o più progetti:

    - Per specificare una set di regole per un singolo progetto, selezionare il nome del progetto.

    - Per specificare una set di regole per più progetti, tenere premuto **Ctrl** e selezionare i nomi dei progetti.

    - Per specificare tutti i progetti nella soluzione, tenere premuto **MAIUSC** e fare clic nell'elenco di progetti.

5. Selezionare il **del Set di regole** campo di un progetto e quindi selezionare il nome della regola impostata che si desidera applicare.

## <a name="see-also"></a>Vedere anche

- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)