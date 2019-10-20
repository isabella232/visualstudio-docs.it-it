---
title: Usare i criteri di archiviazione dell'analisi del codice
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b5a165d2f0f3c17a91775d2d37eadf32307d248
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649416"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procedura: applicare codice gestibile con criteri di archiviazione dell'analisi del codice

Gli sviluppatori possono usare lo strumento metrica codice per misurare la complessità e la gestibilità del codice, ma non è possibile richiamare la metrica del codice come parte di un criterio di archiviazione. Tuttavia, è possibile abilitare le regole di analisi del codice per verificare la conformità del codice con gli standard di metrica del codice e applicare le regole attraverso i criteri di archiviazione. Per altre informazioni sulle metriche del codice, vedere [valori della metrica](../code-quality/code-metrics-values.md)del codice.

È possibile abilitare la profondità dell'ereditarietà, l'accoppiamento di classi, l'indice di gestibilità e le regole di complessità per applicare codice gestibile tramite criteri di archiviazione dell'analisi del codice. Tutte e quattro queste regole sono disponibili nella categoria "regole di gestibilità" nell'editor dei criteri di analisi del codice.

Gli amministratori del controllo della versione di Team Foundation possono aggiungere le regole di gestibilità dell'analisi del codice ai requisiti dei criteri di archiviazione. Questi criteri di archiviazione richiedono agli sviluppatori di eseguire l'analisi del codice in base a queste modifiche della regola prima di avviare un'archiviazione.

## <a name="to-open-the-code-analysis-policy-editor"></a>Per aprire l'editor dei criteri di analisi del codice

1. In **Team Explorer**fare clic con il pulsante destro del mouse sul progetto, scegliere **Impostazioni progetto**, quindi fare clic su **controllo del codice sorgente**.

     Verrà visualizzata la finestra di dialogo **controllo del codice sorgente** .

2. Nella scheda **criteri di archiviazione** fare clic su **Aggiungi**.

     Verrà visualizzata la finestra **di dialogo Aggiungi criteri di archiviazione** .

3. Nell'elenco **criteri di archiviazione** selezionare la casella di controllo **analisi codice** , quindi fare clic su **OK**.

     Verrà visualizzata la finestra di dialogo **Editor criteri di analisi codice** .

## <a name="to-enable-code-analysis-maintainability-rules"></a>Per abilitare le regole di gestibilità dell'analisi codice

1. Nella finestra di dialogo **Editor criteri di analisi codice** , in **Impostazioni regola**, espandere il nodo **regole di gestibilità** .

2. Selezionare le caselle di controllo per le regole seguenti:

   - Profondità dell'ereditarietà: **CA1501 AvoidExcessiveInheritance** -soglia: avviso a più di 5 livelli di profondità

   - Complessità: **CA1502 AvoidExcessiveComplexity** -soglia: avviso a più di 25

   - Indice di gestibilità: **CA1505 AvoidUnmaintainableCode** -soglia: avviso con meno di 20

   - Accoppiamento della classe: **CA1506 AvoidExcessiveClassCoupling** -Threshold: avviso a più di 80 per una classe e più di 30 per un metodo

     Inoltre, se si desidera una violazione della regola per impedire una compilazione riuscita, selezionare la casella di controllo **Considera avviso come errore** accanto alla descrizione della regola.

3. Fare clic su **OK**. I nuovi criteri di archiviazione si applicano ora alle archiviazioni future.

## <a name="see-also"></a>Vedere anche

- [Valori della metrica del codice](../code-quality/code-metrics-values.md)
- [Creazione e utilizzo di criteri di archiviazione dell'analisi del codice](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
