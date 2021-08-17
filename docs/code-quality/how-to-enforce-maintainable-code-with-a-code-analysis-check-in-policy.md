---
title: Usare criteri di archiviazione dell'analisi del codice
ms.date: 11/04/2016
description: Informazioni su come usare i criteri di archiviazione dell'analisi codice per verificare che il codice sia conforme agli standard di ereditarietà, accoppiamento di classi, manutenibilità e complessità.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 4188a9d12daa5294e6771d3a1b4fc4a37b044521
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091305"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procedura: Applicare codice gestibile con criteri di archiviazione dell'analisi del codice

Gli sviluppatori possono usare lo strumento Metriche codice per misurare la complessità e la manutenibilità del codice, ma non è possibile richiamare Metriche codice come parte di criteri di archiviazione. Tuttavia, è possibile abilitare Code Analysis che verificano la conformità del codice con gli standard delle metriche del codice e applicano le regole tramite i criteri di archiviazione. Per altre informazioni sulle metriche del codice, vedere [Valori delle metriche del codice.](../code-quality/code-metrics-values.md)

È possibile abilitare le regole Depth of Inheritance, Class Coupling, Maintainability Index e Complexity per applicare il codice gestibile tramite un criterio di Code Analysis di archiviazione. Tutte e quattro queste regole si trovano nella categoria "Regole di manutenibilità" nell'editor Code Analysis criteri.

Gli amministratori del controllo della versione per Team Foundation possono aggiungere Code Analysis regole di manutenibilità ai requisiti dei criteri di archiviazione. Questi criteri di archiviazione richiedono agli sviluppatori di eseguire Code Analysis in base a queste modifiche alle regole prima di avviare un'archiviazione.

## <a name="to-open-the-code-analysis-policy-editor"></a>Per aprire l'editor Code Analysis criteri

1. In **Team Explorer** fare clic con il pulsante destro del mouse sul **progetto, scegliere Project Impostazioni** e quindi fare clic su Controllo del codice **sorgente**.

     Verrà **visualizzata la finestra di** dialogo Controllo del codice sorgente .

2. Nella scheda **Criteri di archiviazione** fare clic su **Aggiungi**.

     Verrà **visualizzata la finestra di dialogo Aggiungi** criteri di archiviazione .

3. **Nell'elenco Criteri di archiviazione**  selezionare la Code Analysis e quindi fare clic su **OK.**

     Verrà **visualizzata Code Analysis finestra di dialogo Editor** criteri di configurazione.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Per abilitare le regole di manutenibilità dell'analisi del codice

1. Nella finestra **Code Analysis editor** dei criteri, in **Regole Impostazioni** espandere il nodo Regole **di manutenibilità.**

2. Selezionare le caselle di controllo per le regole seguenti:

   - Profondità dell'ereditarietà: **CA1501 AvoidExcessiveInheritance** - Threshold: Warning at more than 5 levels deep

   - Complessità: **CA1502 AvoidExcessiveComplexity** - Threshold: Warning at more than 25

   - Indice di manutenibilità: **CA1505 AvoidUnmaintainableCode** - Soglia: Avviso inferiore a 20

   - Accoppiamento di classi: **CA1506 AvoidExcessiveClassCoupling** - Threshold: Warning at more than 80 for a class and more than 30 for a method

     Inoltre, se si vuole che una violazione della  regola impedisci una compilazione corretta, selezionare la casella di controllo Considera avviso come errore accanto alla descrizione della regola.

3. Fare clic su **OK**. I nuovi criteri di archiviazione si applicano ora alle archiviazioni future.

## <a name="see-also"></a>Vedi anche

- [Valori delle metriche del codice](../code-quality/code-metrics-values.md)
- [Creazione e uso dei criteri di archiviazione dell'analisi codice](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
