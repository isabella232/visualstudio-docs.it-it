---
title: Configurare Code Analysis
ms.date: 04/04/2018
description: Informazioni su come configurare il set di regole che Visual Studio'analisi del codice legacy. Vedere come applicare un set di regole a uno o più progetti in una soluzione.
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
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 645441b8961ca84534bd9f4a503189ceb2cb5ab3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122150"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Procedura: Configurare l'analisi legacy per il codice gestito

In Visual Studio è possibile scegliere da un elenco di set di regole di analisi del codice [da](../code-quality/rule-set-reference.md) applicare a un progetto di codice gestito. Per impostazione predefinita, il set **di regole Microsoft Minimum Recommended Rules** è selezionato, ma è possibile applicare un set di regole diverso, se lo si desidera. I set di regole possono essere applicati a uno o più progetti in una soluzione.

> [!NOTE]
> Questo articolo si applica all'analisi legacy e [non .NET Compiler Platform analizzatori di codice basati su .](use-roslyn-analyzers.md)

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurare un set di regole per un progetto .NET Framework

1. Aprire la **Code Analysis** nella pagina delle proprietà del progetto. È possibile precedere in uno dei modi seguenti:

   - In **Esplora soluzioni** scegliere il progetto. Sulla barra dei menu selezionare **Analizza**  >  **Configura Code Analysis**  >  **\<projectname> per**.

   - Fare clic con il pulsante destro del mouse **Esplora soluzioni** progetto in e **scegliere** Proprietà e quindi selezionare la **Code Analysis** predefinita.

2. Negli elenchi **Configurazione e** **Piattaforma** scegliere la configurazione della build e la piattaforma di destinazione.

::: moniker range="vs-2017"

3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato usando la configurazione selezionata, selezionare Abilita Code Analysis **in Compilazione**. È anche possibile eseguire manualmente l'analisi del codice **selezionando** Analizza Code Analysis  >    >  **esegui Code Analysis in \<projectname>**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato usando la configurazione selezionata, selezionare Esegui alla **compilazione** nella **sezione Analizzatori binari.** È anche possibile eseguire manualmente l'analisi del codice legacy. Per altre informazioni, vedere [Procedura:](how-to-run-legacy-code-analysis-manually-for-managed-code.md) Eseguire le Code Analysis legacy manualmente per il codice gestito.

::: moniker-end

4. Per visualizzare gli avvisi dal codice generato, deselezionare la **casella di controllo** Elimina risultati dal codice generato.

    > [!NOTE]
    > Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello e non verrà sovrascritto.

::: moniker range="vs-2017"

5. **Nell'elenco Esegui questo set di regole** eseguire una delle operazioni seguenti:

::: moniker-end

::: moniker range=">=vs-2019"

5. **Nell'elenco Regole attive** eseguire una delle operazioni seguenti:

::: moniker-end

   - Selezionare il set di regole che si vuole usare.

   - Selezionare **\<Browse>** questa opzione per trovare un set di regole personalizzato esistente non presente nell'elenco.

   - Definire un [set di regole personalizzato.](../code-quality/how-to-create-a-custom-rule-set.md)

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Specificare set di regole per più progetti in una soluzione

Per impostazione predefinita, a tutti i progetti gestiti di una soluzione viene assegnato il set di regole di analisi del codice *Microsoft Minimum Recommended Rules.* È possibile modificare i set di regole assegnati ai progetti di una soluzione nella finestra **di** dialogo Proprietà della soluzione.

1. Aprire la soluzione in Visual Studio.

2. Nel menu **Analizza** selezionare Configura **Code Analysis per la soluzione**.

3. Se necessario, espandere **Proprietà comuni** e quindi selezionare **Code Analysis Impostazioni**.

4. È possibile specificare un set di regole per uno o più progetti:

    - Per specificare un set di regole per un singolo progetto, scegliere il nome del progetto.

    - Per specificare un set di regole per più progetti, selezionare **CTRL** e i nomi dei progetti.

    - Per specificare tutti i progetti nella soluzione, selezionare **MAIUSC e** l'elenco di progetti.

5. Selezionare il **campo Set di** regole di un progetto e quindi selezionare il nome del set di regole da applicare.

## <a name="see-also"></a>Vedi anche

- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)
