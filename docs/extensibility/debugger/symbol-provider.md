---
title: Provider di simboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea31d6bcd8c055756a49c46f8fb4b3f377aaade8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912896"
---
# <a name="symbol-provider"></a>Provider di simboli
Un'implementazione dell'analizzatore di espressioni deve accedere alle informazioni di debug sui simboli generate dal compilatore del linguaggio per poter valutare variabili ed espressioni. Esegue l'operazione utilizzando le interfacce di un provider di simboli (SP), chiamato anche un gestore di simboli.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce stored procedure per codice gestito e codice nativo usando il formato di file di simboli di DataBase di programma (PDB). A meno che non vi è un forte necessaria al programma usare i simboli archiviati in un formato personalizzato, è consigliabile usare il Service Pack forniti da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="implementation-notes"></a>Note di implementazione
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug che prevede di comunicare con il Service Pack utilizzando le interfacce di Common Language Runtime (CLR). Di conseguenza, un Service Pack che verranno usate con i motori di debug di Visual Studio deve supportare il CLR. Un elenco completo di tutte le interfacce di debug di CLR è reperibile in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].

 Se il SP userà solo il motore di debug personalizzato, è possibile implementare stored procedure nel modo desiderato a seconda delle esigenze del motore di debug.

## <a name="see-also"></a>Vedere anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)