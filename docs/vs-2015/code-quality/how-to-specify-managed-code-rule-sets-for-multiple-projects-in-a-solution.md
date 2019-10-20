---
title: 'Procedura: specificare set di regole di codice gestito per più progetti in una soluzione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5333f6133dd3fd56077c14d6e56cd6fdada4404
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656416"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Procedura: specificare set di regole di codice gestito per più progetti in una soluzione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per impostazione predefinita, a tutti i progetti gestiti di una soluzione viene assegnato il *set*di regole di analisi del codice per le regole minime consigliate di Microsoft. È possibile modificare i set di regole assegnati ai progetti di una soluzione nella finestra di dialogo proprietà per la soluzione.

> [!NOTE]
> Per impostazione predefinita, l'analisi del codice del progetto non viene eseguita come passaggio di compilazione. Per abilitare l'analisi del codice come passaggio di compilazione, vedere [procedura: configurare l'analisi del codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Per specificare un set di regole per più progetti in una soluzione di codice gestito

1. In [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. Aprire la soluzione [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] o [!INCLUDE[vsPro](../includes/vspro-md.md)].

2. Nel menu **analizza** fare clic su **Configura analisi codice per la soluzione**.

3. Se necessario, espandere **Proprietà comuni**, quindi fare clic su **Impostazioni analisi codice**.

4. È possibile specificare un set di regole per uno o più progetti.

    - Per specificare un set di regole per un singolo progetto, fare clic sul nome del progetto.

    - Per specificare un set di regole per più progetti, tenere premuto CTRL e fare clic sui nomi del progetto.

    - Per specificare tutti i progetti nella soluzione, tenere premuto MAIUSC e fare clic nell'elenco progetto.

5. Fare clic sul campo **set di regole** di un progetto e quindi fare clic sul nome del set di regole che si desidera applicare.
