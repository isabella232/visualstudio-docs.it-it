---
title: Compatibilità delle versioni di criteri di controllo dell'analisi del codice | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 840a12e7f4c0e3853e885a803dea5a92e05a5a27
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261482"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se è necessario valutare e creare codice check-in Criteri di analisi usino versioni diverse di [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], è necessario conoscere le differenze nella procedura [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] e [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] valutare i criteri di controllo.  
  
## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilità delle versioni di valutazione di criteri di archiviazione  
  
-   Quando i criteri di controllo dell'analisi del codice vengono valutati [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], eventuali regole presenti in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ma non esistono nel [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] vengono ignorati.  
  
-   Quando i criteri di controllo dell'analisi del codice vengono valutati [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], tutte le regole sono esclusive di [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] vengono ignorati.  
  
-   Se i criteri di controllo dell'analisi codice specificano gli assembly di regole, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] Ignora tutte le regole che vengono specificate dagli assembly che non riconosce.  
  
-   Se i criteri di controllo dell'analisi codice specificano gli assembly di regole che [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] non riconosce, viene visualizzato un messaggio.  
  
## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilità delle versioni per la creazione di criteri di archiviazione  
  
-   Se è stato creato un criterio di controllo dell'analisi codice usando il [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] versione di [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], non è possibile utilizzare il [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] versione di [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] per modificarlo. E inoltre [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] non è possibile valutare i criteri.  
  
-   Se è stato creato un criterio di controllo dell'analisi codice usando [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] nel [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], è possibile usare [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] nelle [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] per modificarlo, quindi i criteri possa anche essere valutato [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]. Dopo aver modificato i criteri usando [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] nel [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], è non possibile modificare i criteri non sono più usando [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]. [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] può valutare i criteri senza problemi con i nomi sicuri non corrispondenti.  
  
-   Per creare un criterio di controllo dell'analisi codice con impostazioni delle regole valide per entrambi [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] e [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], è necessario creare i criteri in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], apportare tutte le modifiche necessarie e salvare il criterio. Se le modifiche alle regole sono disponibili solo nel [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], modificare e salvare i criteri in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)].  
  
     Dopo aver salvato i criteri in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], non è più è possibile modificare le impostazioni per le regole esistenti in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] solo.



