---
title: Configurare l'analisi del codiceConfigure Code Analysis
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 98db7cda02495d207d6e9387341173ea2efe22ca
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431352"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Procedura: configurare l'analisi legacy per il codice gestitoHow to: Configure legacy analysis for managed code

In Visual Studio è possibile scegliere da un elenco di set di [regole](../code-quality/rule-set-reference.md) di analisi del codice da applicare a un progetto di codice gestito. Per impostazione predefinita, il set di **regole Regole minime consigliate Microsoft** è selezionato, ma è possibile applicare un set di regole diverso, se lo si desidera. I set di regole possono essere applicati a uno o più progetti in una soluzione.

> [!NOTE]
> In questo articolo si applica all'analisi legacy e non agli [analizzatori di codice basati su piattaforma del compilatore .NET](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurare un set di regole per un progetto .NET Framework

1. Aprire la scheda **Analisi codice** nelle pagine delle proprietà del progetto. È possibile precedere in uno dei modi seguenti:

   - In **Esplora soluzioni**selezionare il progetto. Sulla barra dei menu selezionare **Analizza analisi** > **codice** > di configurazione**per \<nomeprogetto>**.

   - Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e selezionare **Proprietà**, quindi selezionare la scheda **Analisi codice.**

2. Negli elenchi **Configurazione** e **Piattaforma** selezionare la configurazione di compilazione e la piattaforma di destinazione.

::: moniker range="vs-2017"

3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato utilizzando la configurazione selezionata, selezionare **Abilita analisi codice durante la compilazione**. È inoltre possibile eseguire manualmente l'analisi del codice selezionando **Analizza** > analisi codice di esecuzione dell'analisi**Run Code Analysis** > del**codice su \<nomeprogetto>**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato utilizzando la configurazione selezionata, selezionare Esegui in base alla **compilazione** nella sezione **Analizzatori binari.** È anche possibile eseguire manualmente l'analisi del codice legacy, vedere [Procedura: eseguire manualmente l'analisi del codice legacy per il codice gestito](how-to-run-legacy-code-analysis-manually-for-managed-code.md) per ulteriori dettagli.

::: moniker-end

4. Per visualizzare gli avvisi dal codice generato, deselezionare la casella di controllo **Elimina risultati dal codice generato.**

    > [!NOTE]
    > Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello e non verrà sovrascritto.

::: moniker range="vs-2017"

5. Nell'elenco **Esegui set di regole** eseguire una delle operazioni seguenti:

::: moniker-end

::: moniker range=">=vs-2019"

5. Nell'elenco **Regole attive** eseguire una delle operazioni seguenti:

::: moniker-end

   - Selezionare il set di regole che si desidera utilizzare.

   - Selezionare Sfoglia ** \<>** per trovare un set di regole personalizzato esistente non presente nell'elenco.

   - Definire un set di [regole personalizzato](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Specificare i set di regole per più progetti in una soluzioneSpecify rule sets for multiple projects in a solution

Per impostazione predefinita, a tutti i progetti gestiti di una soluzione viene assegnato il set di regole di analisi del codice *Regole minime Microsoft.By* default, all the managed projects of a solution are assigned the Microsoft Minimum Recommended Rules code analysis rule set. È possibile modificare i set di regole assegnati ai progetti di una soluzione nella finestra di dialogo **Proprietà** per la soluzione.

1. Aprire la soluzione in Visual Studio.

2. Scegliere Configura analisi **codice per soluzione dal**menu **Analizza** .

3. Se necessario, espandere **Proprietà comuni**, quindi selezionare Impostazioni **analisi codice**.

4. È possibile specificare un set di regole per uno o più progetti:You can specify a rule set for one or more projects:

    - Per specificare un set di regole per un singolo progetto, selezionare il nome del progetto.

    - Per specificare un set di regole per più progetti, tenere premuto **CTRL** e selezionare i nomi dei progetti.

    - Per specificare tutti i progetti nella soluzione, tenere premuto **Maiusc** e fare clic nell'elenco dei progetti.

5. Selezionare il campo **Set** di regole di un progetto, quindi selezionare il nome del set di regole che si desidera applicare.

## <a name="see-also"></a>Vedere anche

- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)
