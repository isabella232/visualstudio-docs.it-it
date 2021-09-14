---
title: Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice
ms.date: 11/04/2016
description: Informazioni su come Team System 2008 Team Foundation Server e Team Foundation Server 2010 valutano Visual Studio criteri di archiviazione in modo diverso.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 1cd049a8e2aea94e6dc3b581c5b6ca8ccf3ab4e8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631800"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice

Se è necessario valutare e creare criteri di archiviazione dell'analisi del codice usando versioni diverse di , è necessario conoscere le differenze nella modalità e nella valutazione [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] dei criteri di [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] archiviazione.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilità delle versioni per la valutazione dei Check-In versione

- Quando i criteri di archiviazione dell'analisi codice vengono valutati in , tutte le regole esistenti in ma che [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] non esistono in vengono [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignorate.

- Quando i criteri di archiviazione dell'analisi codice vengono valutati in , tutte le nuove regole esclusive [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] di [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vengono ignorate.

- Se i criteri di archiviazione dell'analisi codice specificano assembly di regole, ignora tutte le regole specificate dagli assembly [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] che non riconosce.

- Se i criteri di archiviazione dell'analisi codice specificano assembly di regole che non [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] riconoscono, viene visualizzato un messaggio.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilità delle versioni per la creazione Check-In criteri

- Se sono stati creati criteri di archiviazione dell'analisi codice usando la versione di , non è possibile [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] usare la versione di per [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] modificarli. Inoltre, non [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] può valutare i criteri.

- Se sono stati creati criteri di archiviazione dell'analisi codice usando in , è possibile usare in per modificarli e i criteri possono [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] anche essere [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] valutati da [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] . Dopo aver modificato i criteri usando in , non è più possibile [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] modificare i criteri usando in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] . [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] può valutare i criteri senza problemi con nomi sicuri non corrispondenti.

- Per creare criteri di archiviazione dell'analisi codice con le impostazioni delle regole valide per e , è necessario creare i criteri in , apportare tutte le modifiche necessarie e [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] salvare i [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] criteri. Se le modifiche alle regole esistono solo in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , è possibile modificare e salvare i criteri in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] .

   Dopo aver salvato i criteri in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , non è più possibile modificare le impostazioni per le regole esistenti solo in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] .
