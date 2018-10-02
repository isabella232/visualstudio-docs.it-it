---
title: Provider di simboli | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09fbe350afff983bb5fefe880104201441430c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526447"
---
# <a name="symbol-provider"></a>Provider di simboli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Provider di simboli](https://docs.microsoft.com/visualstudio/extensibility/debugger/symbol-provider).  
  
Un'implementazione dell'analizzatore di espressioni deve accedere alle informazioni di debug sui simboli generate dal compilatore del linguaggio per poter valutare variabili ed espressioni. Esegue l'operazione utilizzando le interfacce di un provider di simboli (SP), chiamato anche un gestore di simboli.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornisce stored procedure per codice gestito e codice nativo usando il formato di file di simboli di DataBase di programma (PDB). A meno che non vi è un forte necessaria al programma usare i simboli archiviati in un formato personalizzato, è consigliabile usare il Service Pack forniti da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="implementation-notes"></a>Note di implementazione  
 Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] motori di debug che prevede di comunicare con il Service Pack utilizzando le interfacce di Common Language Runtime (CLR). Di conseguenza, un Service Pack che verranno usate con i motori di debug di Visual Studio deve supportare il CLR. Un elenco completo di tutte le interfacce di debug di CLR è reperibile in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)].  
  
 Se il SP userà solo il motore di debug personalizzato, è possibile implementare stored procedure nel modo desiderato a seconda delle esigenze del motore di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)

