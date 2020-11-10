---
title: Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice
ms.date: 11/04/2016
description: Informazioni sul modo in cui Team System 2008 Team Foundation Server e Team Foundation Server 2010 valutano i criteri di archiviazione di Visual Studio in modo diverso.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 3a681f510da270bc22ae4bc983103f9a5735a127
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436875"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice

Se è necessario valutare e creare criteri di archiviazione dell'analisi codice utilizzando versioni diverse di [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , è necessario comprendere le differenze tra la modalità [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] e la valutazione dei criteri di [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] archiviazione.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilità tra versioni per la valutazione di criteri di Check-In

- Quando si valutano i criteri di archiviazione dell'analisi del codice in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , tutte le regole esistenti in, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ma non esistono in, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vengono ignorate.

- Quando si valutano i criteri di archiviazione dell'analisi del codice in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , tutte le nuove regole esclusive di [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vengono ignorate.

- Se i criteri di archiviazione dell'analisi del codice specificano gli assembly delle regole, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] Ignora tutte le regole specificate dagli assembly non riconosciute.

- Se i criteri di archiviazione dell'analisi del codice specificano gli assembly di regole che [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] non riconoscono, viene visualizzato un messaggio.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilità tra le versioni per la creazione di criteri di Check-In

- Se è stato creato un criterio di archiviazione dell'analisi del codice utilizzando la [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] versione di [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , non è possibile utilizzare la [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] versione di [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] per modificarlo. Inoltre, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] non è in grado di valutare i criteri.

- Se è stato creato un criterio di archiviazione dell'analisi del codice usando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , è possibile usare [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] per modificarlo e il criterio può essere valutato anche da [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] . Dopo aver modificato il criterio usando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , non è più possibile modificare il criterio usando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] . [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] consente di valutare i criteri senza problemi con nomi sicuri non corrispondenti.

- Per creare criteri di archiviazione dell'analisi del codice con le impostazioni delle regole che si applicano sia a che a [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , è necessario creare i criteri in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , apportare tutte le modifiche necessarie e salvare il criterio. Se le modifiche alle regole sono disponibili solo in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , modificare e salvare il criterio in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] .

   Dopo aver salvato il criterio in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , non è più possibile modificare le impostazioni per le regole presenti [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] solo in.
