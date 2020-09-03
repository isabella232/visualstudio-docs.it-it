---
title: "Procedura: applicare codice gestibile con criteri di archiviazione dell'analisi del codice | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d54ca9a31e8a1bbd2496bf8689a119e53580c79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660215"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procedura: Applicare codice di facile manutenibilità con criteri di archiviazione dell'analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli sviluppatori possono usare lo strumento metrica codice per misurare la complessità e la gestibilità del codice, ma non possono richiamare la metrica del codice come parte di un criterio di archiviazione. Tuttavia, un team può abilitare le regole di analisi del codice che verificano la conformità del codice con gli standard di metrica del codice e applicano le regole attraverso i criteri di archiviazione. Per altre informazioni sulle metriche del codice, vedere [valori della metrica](../code-quality/code-metrics-values.md)del codice.

 Gli sviluppatori possono abilitare la profondità dell'ereditarietà, l'accoppiamento delle classi, l'indice di gestibilità e le regole di complessità per applicare codice gestibile attraverso i criteri di archiviazione dell'analisi del codice. Tutte e quattro queste regole sono disponibili nella categoria "regole di gestibilità" nell'editor dei criteri di analisi del codice.

 Gli amministratori del controllo della versione per [!INCLUDE[esprfound](../includes/esprfound-md.md)] possono aggiungere le regole di gestibilità dell'analisi del codice ai requisiti dei criteri di archiviazione. Questi criteri di archiviazione richiedono agli sviluppatori di eseguire l'analisi del codice in base a queste modifiche della regola prima di avviare un'archiviazione.

### <a name="to-open-the-code-analysis-policy-editor"></a>Per aprire l'editor dei criteri di analisi del codice

1. In **Team Explorer**fare clic con il pulsante destro del mouse sul progetto team, scegliere **Impostazioni progetto team**, quindi fare clic su **controllo del codice sorgente**.

     Verrà visualizzata la finestra di dialogo **controllo del codice sorgente** .

2. Nella scheda **criteri di archiviazione** fare clic su **Aggiungi**.

     Verrà visualizzata la finestra **di dialogo Aggiungi criteri di archiviazione** .

3. Nell'elenco **criteri di archiviazione** selezionare la casella di controllo **analisi codice** , quindi fare clic su **OK**.

     Verrà visualizzata la finestra di dialogo **Editor criteri di analisi codice** .

### <a name="to-enable-code-analysis-maintainability-rules"></a>Per abilitare le regole di gestibilità dell'analisi codice

1. Nella finestra di dialogo **Editor criteri di analisi codice** , in **Impostazioni regola**, espandere il nodo **regole di gestibilità** .

2. Selezionare le caselle di controllo per le regole seguenti:

    - Profondità dell'ereditarietà: **CA1501 AvoidExcessiveInheritance** -soglia: avviso a più di 5 livelli di profondità

    - Complessità: **CA1502 AvoidExcessiveComplexity** -soglia: avviso a più di 25

    - Indice di gestibilità: **CA1505 AvoidUnmaintainableCode** -soglia: avviso con meno di 20

    - Accoppiamento della classe: **CA1506 AvoidExcessiveClassCoupling** -Threshold: avviso a più di 80 per una classe e più di 30 per un metodo

    - Inoltre, se si desidera che una violazione della regola impedisca una compilazione, selezionare la casella di controllo **Considera avviso come errore** accanto alla descrizione della regola.

3. Fare clic su **OK**. I nuovi criteri di archiviazione si applicano ora alle archiviazioni future.

## <a name="see-also"></a>Vedere anche
 [Valori della metrica del codice](../code-quality/code-metrics-values.md) [creazione e utilizzo di criteri di archiviazione dell'analisi del codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
