---
title: 'Procedura: Impostare le proprietà di analisi codice per progetti C-c + + | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 4ebed266924861dac4bfc9e316a56907dbd11534
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964762"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Procedura: Impostare le proprietà di analisi codice per progetti C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile configurare le regole utilizza lo strumento di analisi codice per analizzare il codice in ogni configurazione del progetto. Inoltre, è possibile indirizzare analisi del codice per eliminare gli avvisi del codice che è stato generato e aggiunto al progetto da uno strumento di terze parti.  
  
## <a name="code-analysis-property-page"></a>Pagina proprietà dell'analisi codice  
 Il **analisi del codice** pagina delle proprietà contiene tutte le impostazioni di configurazione di analisi di codice per un progetto. Per aprire la pagina proprietà di analisi codice per un progetto in **Esplora soluzioni**, fare clic sul progetto e quindi fare clic su **proprietà**. Successivamente, espandere **le proprietà di configurazione** e selezionare il **analisi del codice** scheda.  
  
## <a name="project-configuration-and-platform"></a>Piattaforma e configurazione del progetto  
 Il **Configuration** elenco e **piattaforma** elenco consente di applicare le impostazioni di analisi di codice diversi in base a combinazioni di configurazione e piattaforma di progetto diverso. Ad esempio, è possibile indirizzare compilazioni di analisi del codice per applicare un set di regole per il progetto per il debug e compila un set diverso per il rilascio.  
  
## <a name="enabling-code-analysis"></a>Abilitazione dell'analisi del codice  
 È possibile decidere se abilitare l'analisi del codice per il progetto selezionando **Abilita analisi codice per C/C++ in fase di compilazione**. In combinazione con il **configurazione** elenco, è possibile, ad esempio, decidere disabilitare l'analisi codice per le compilazioni di debug e abilitare per versione le compilazioni.  
  
 Se il progetto contiene codice gestito, è possibile decidere se abilitare o disabilitare l'analisi codice selezionando **Abilita analisi codice su compilazione**.  
  
 Analisi del codice è progettato per aiutarti a migliorare la qualità del codice ed evitare errori comuni. Pertanto, valutare attentamente se disabilitare l'analisi del codice. È in genere preferibile disabilitare il set di regole o regole singole che non si desidera applicare al progetto.  
  
## <a name="generated-code"></a>Codice generato  
 Gli sviluppatori spesso utilizzano strumenti che consentono di sviluppare rapidamente applicazioni. Questi strumenti è possono generare codice che viene aggiunto al progetto. Si potrebbe voler visualizzare le violazioni delle regole di analisi del codice consente di individuare il codice generato. Tuttavia, si potrebbe non si desidera visualizzarli se non si desidera mantenere il codice.  
  
 Il **eliminare i risultati del codice generato** casella di controllo la **generali** pagina delle proprietà consente di specificare se si desidera visualizzare gli avvisi dell'analisi codice dal codice gestito che viene generato da uno strumento di terze parti .  
  
## <a name="rule-sets"></a>Set di regole  
 Se il progetto contiene codice gestito, è possibile selezionare le regole da applicare in un'analisi del codice tramite la selezione di una set di regole dal **eseguire questo set di regole** elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Avvisi dell'analisi codice per C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)
