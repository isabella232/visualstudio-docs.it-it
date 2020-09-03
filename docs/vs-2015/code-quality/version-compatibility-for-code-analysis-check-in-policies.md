---
title: Compatibilità tra le versioni per i criteri di archiviazione dell'analisi del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 075981569cbee05e90afe17b3afc9558d7bbb270
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609309"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se è necessario valutare e creare criteri di archiviazione dell'analisi codice utilizzando versioni diverse di [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , è necessario comprendere le differenze tra la modalità [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] e la valutazione dei criteri di [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] archiviazione.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilità tra le versioni per la valutazione dei criteri di archiviazione

- Quando si valutano i criteri di archiviazione dell'analisi del codice in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , tutte le regole esistenti in, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ma non esistono in, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] vengono ignorate.

- Quando si valutano i criteri di archiviazione dell'analisi del codice in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , tutte le nuove regole esclusive di [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] vengono ignorate.

- Se i criteri di archiviazione dell'analisi del codice specificano gli assembly delle regole, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] Ignora tutte le regole specificate dagli assembly non riconosciute.

- Se i criteri di archiviazione dell'analisi del codice specificano gli assembly di regole che [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] non riconoscono, viene visualizzato un messaggio.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilità tra le versioni per la creazione di criteri di archiviazione

- Se è stato creato un criterio di archiviazione dell'analisi del codice utilizzando la [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] versione di [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , non è possibile utilizzare la [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] versione di [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] per modificarlo. Inoltre, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] non è in grado di valutare i criteri.

- Se è stato creato un criterio di archiviazione dell'analisi del codice usando [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , è possibile usare [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] per modificarlo e il criterio può essere valutato anche da [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] . Dopo aver modificato il criterio usando [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , non è più possibile modificare il criterio usando [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] . [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] consente di valutare i criteri senza problemi con nomi sicuri non corrispondenti.

- Per creare criteri di archiviazione dell'analisi del codice con le impostazioni delle regole che si applicano sia a che a [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , è necessario creare i criteri in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , apportare tutte le modifiche necessarie e salvare il criterio. Se le modifiche alle regole sono disponibili solo in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , modificare e salvare il criterio in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] .

     Dopo aver salvato il criterio in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , non è più possibile modificare le impostazioni per le regole presenti [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] solo in.
