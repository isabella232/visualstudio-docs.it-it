---
title: 'Procedura: Impostare le proprietà di analisi codice per progetti C/C++'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 72866618383382389ad5e5706ae2a0999c89c346
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923979"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Procedura: Impostare le proprietà di analisi codice per progetti C/C++
È possibile configurare le regole utilizzate dallo strumento di analisi del codice per analizzare il codice in ogni configurazione del progetto. Inoltre, è possibile indirizzare l'analisi del codice in modo da non visualizzare gli avvisi dal codice generato e aggiunto al progetto da uno strumento di terze parti.

## <a name="code-analysis-property-page"></a>Pagina delle proprietà dell'analisi del codice
Nella pagina delle proprietà **analisi codice** sono contenute tutte le impostazioni di configurazione dell'analisi del codice per un progetto. Per aprire la pagina delle proprietà analisi codice per un progetto in **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**. Successivamente, espandere **proprietà di configurazione** e selezionare la scheda **analisi codice** .

## <a name="project-configuration-and-platform"></a>Configurazione e piattaforma del progetto
L'elenco di **configurazione** e l'elenco di **piattaforme** consentono di applicare diverse impostazioni di analisi del codice a diverse combinazioni di configurazioni di progetto e piattaforme. Ad esempio, è possibile indirizzare l'analisi del codice per applicare un set di regole al progetto per le compilazioni di debug e un set diverso per le build di rilascio.

## <a name="enabling-code-analysis"></a>Abilitazione dell'analisi codice
È possibile decidere se abilitare l'analisi del codice per il progetto selezionando **Abilita analisi codice per CC++ /on compilazione**. In combinazione con l'elenco di **configurazione** , è possibile, ad esempio, decidere di disabilitare l'analisi del codice per le compilazioni di debug e abilitarla per le build di rilascio.

Se il progetto contiene codice gestito, è possibile decidere se abilitare o disabilitare l'analisi del codice selezionando **Abilita analisi codice durante la compilazione**.

L'analisi del codice è progettata per contribuire a migliorare la qualità del codice ed evitare problemi comuni. Pertanto, valutare attentamente se disabilitare l'analisi del codice. È in genere preferibile disabilitare i set di regole o le singole regole che non si desidera applicare al progetto.

## <a name="generated-code"></a>Codice generato
Gli sviluppatori utilizzano spesso strumenti che consentono di sviluppare rapidamente applicazioni. Questi strumenti possono generare codice aggiunto al progetto. È possibile che si desideri visualizzare le violazioni della regola individuate dall'analisi del codice nel codice generato. Tuttavia, è possibile che non si desideri visualizzarli se non si desidera gestire il codice.

La casella di controllo non **visualizzare i risultati del codice generato** nella pagina delle proprietà **generale** consente di specificare se si desidera visualizzare gli avvisi di analisi del codice dal codice gestito generato da uno strumento di terze parti.

## <a name="rule-sets"></a>Set di regole
Se il progetto contiene codice gestito, è possibile selezionare le regole da applicare in un'analisi del codice selezionando un set di regole nell'elenco **Esegui questo set di regole** .

## <a name="see-also"></a>Vedere anche

- [Analisi della qualità del codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)
- [Avvisi dell'analisi codice per C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)