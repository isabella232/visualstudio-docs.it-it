---
title: Risoluzione dei problemi relativi alla metrica di codice | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: "4"
author: erickson-doug
ms.author: douge
manager: douge
ms.openlocfilehash: 6dde34ce4808f21a90fa9d2e37daf7ed88d4e7fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-code-metrics-issues"></a>Risoluzione dei problemi relativi alla metrica codice
Quando si esegue la raccolta della metrica di codice, è possibile che si verifichino alcuni dei problemi seguenti:  
  
-   [Modifiche nei calcoli di complessità del codice di Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Modifiche nei calcoli di complessità del codice di Visual Studio 2010  
 È possibile che, per la stessa funzione, la metrica di complessità del codice calcolata in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] sia diversa dalla metrica calcolata da versioni precedenti di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] nelle situazioni seguenti:  
  
-   La funzione contiene uno o più blocchi catch. Nelle versioni precedenti di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] i blocchi catch non erano inclusi nel calcolo. In [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] la complessità di ogni blocco catch è stata aggiunta alla complessità della funzione.  
  
-   La funzione contiene un'istruzione switch (Select Case in VB). Il compilatore distingue [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] dalle versioni precedenti è può generare codice MSIL diverso per alcune istruzioni switch che contengono casi di fallthrough.  
  
## <a name="see-also"></a>Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)