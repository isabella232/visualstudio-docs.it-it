---
title: Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4757b3a105ff02a92944d9b45e645e2c63a8b81c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587160"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice

Se è necessario valutare e creare criteri di archiviazione dell'analisi del codice utilizzando versioni diverse di [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], è necessario comprendere le differenze tra [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] e [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] valutare i criteri di archiviazione.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilità tra le versioni per la valutazione dei criteri di archiviazione

- Quando i criteri di archiviazione dell'analisi del codice vengono valutati in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], tutte le regole esistenti in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ma che non esistono in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vengono ignorate.

- Quando i criteri di archiviazione dell'analisi del codice vengono valutati in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], tutte le nuove regole esclusive per [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] verranno ignorate.

- Se i criteri di archiviazione dell'analisi del codice specificano gli assembly delle regole, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignora tutte le regole specificate dagli assembly non riconosciute.

- Se i criteri di archiviazione dell'analisi del codice specificano gli assembly di regole che [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] non riconosce, viene visualizzato un messaggio.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilità tra le versioni per la creazione di criteri di archiviazione

- Se è stato creato un criterio di archiviazione dell'analisi del codice usando la versione [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] di [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], non è possibile usare la versione [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] di [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] per modificarla. Inoltre, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] non è in grado di valutare i criteri.

- Se è stato creato un criterio di archiviazione dell'analisi del codice utilizzando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], è possibile utilizzare [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] per modificarlo e il criterio può essere valutato anche da [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Dopo aver modificato il criterio utilizzando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], non è più possibile modificare il criterio utilizzando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] possibile valutare i criteri senza problemi con nomi sicuri non corrispondenti.

- Per creare criteri di archiviazione dell'analisi del codice con le impostazioni delle regole valide per [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] e [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], è necessario creare i criteri in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], apportare tutte le modifiche necessarie e salvare il criterio. Se le modifiche alle regole esistono solo in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], è possibile modificare e salvare il criterio in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   Dopo aver salvato i criteri in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], non è più possibile modificare le impostazioni per le regole presenti solo in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].
