---
title: 'Procedura: specificare i set di regole di codice gestito per più progetti in una soluzione | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 42b04eb88e6edee2d8250ac29a26f4cfe6562a29
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528242"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Procedura: specificare set di regole di codice gestito per più progetti in una soluzione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: specificare Managed Code set di regole per più progetti in una soluzione](https://docs.microsoft.com/visualstudio/code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution).  
  
Per impostazione predefinita, tutti i progetti gestiti di una soluzione vengono assegnati l'analisi del codice Microsoft regole minime *set di regole*. È possibile modificare i set di regole che vengono assegnati ai progetti di una soluzione nella finestra di dialogo proprietà per la soluzione.  
  
> [!NOTE]
>  Per impostazione predefinita, analisi del codice di progetto non viene eseguito come passaggio di compilazione. Per abilitare analisi del codice come passaggio di compilazione, vedere [procedura: Configura analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Per specificare una set di regole per più progetti in una soluzione con codice gestito  
  
1.  In [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. Aprire la soluzione [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] o [!INCLUDE[vsPro](../includes/vspro-md.md)].  
  
2.  Nel **Analyze** menu, fare clic su **Configura analisi codice per la soluzione**.  
  
3.  Se necessario, espandere **proprietà comuni**, quindi fare clic su **impostazioni di analisi codice**.  
  
4.  È possibile specificare una set di regole per uno o più progetti.  
  
    -   Per specificare una set di regole per un singolo progetto, fare clic sul nome del progetto.  
  
    -   Per specificare una set di regole per più progetti, tenere premuto CTRL e fare clic sui nomi di progetto.  
  
    -   Per specificare tutti i progetti nella soluzione, tenere premuto MAIUSC e fare clic nell'elenco di progetto.  
  
5.  Scegliere il **del Set di regole** campo di un progetto e quindi fare clic su imposta il nome della regola che si desidera applicare.



