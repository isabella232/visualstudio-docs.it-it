---
title: Risoluzione dei problemi relativi alla metrica di codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3eda4127e046c7676525f1755f148663f58ec9b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672070"
---
# <a name="troubleshooting-code-metrics-issues"></a>Risoluzione dei problemi relativi alla metrica codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si esegue la raccolta della metrica di codice, è possibile che si verifichino alcuni dei problemi seguenti:

- [Modifiche nei calcoli di complessità del codice di Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Modifiche nei calcoli di complessità del codice di Visual Studio 2010

È possibile che, per la stessa funzione, la metrica di complessità del codice calcolata in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] sia diversa dalla metrica calcolata da versioni precedenti di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] nelle situazioni seguenti:

- La funzione contiene uno o più blocchi catch. Nelle versioni precedenti di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] i blocchi catch non erano inclusi nel calcolo. In [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] la complessità di ogni blocco catch è stata aggiunta alla complessità della funzione.

- La funzione contiene un'istruzione switch (Select Case in VB). Il compilatore distingue [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] dalle versioni precedenti è può generare codice MSIL diverso per alcune istruzioni switch che contengono casi di fallthrough.

## <a name="see-also"></a>Vedere anche

- [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
