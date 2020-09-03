---
title: Provider di simboli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6af1af9d2e178241fa8a5957e18c1a5333fa4b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178893"
---
# <a name="symbol-provider"></a>Provider di simboli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un'implementazione dell'analizzatore di espressioni deve accedere alle informazioni di debug simboliche generate dal compilatore del linguaggio per valutare variabili ed espressioni. Questa operazione viene eseguita tramite l'utilizzo delle interfacce di un provider di simboli (SP), denominato anche gestore di simboli.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornisce SPs per codice gestito e codice nativo utilizzando il formato di file di simboli del DataBase di programma (PDB). A meno che non sia necessario che il programma usi i simboli archiviati in un formato personalizzato, è consigliabile usare SPs fornito da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="implementation-notes"></a>Note sull'implementazione  
 I [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] motori di debug si aspettano di comunicare con SPS usando le interfacce CLR (Common Language Runtime). Di conseguenza, un SP che lavorerà con i motori di debug di Visual Studio deve supportare CLR. Un elenco completo di tutte le interfacce di debug CLR si trova in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] .  
  
 Se il servizio SP funziona solo con il motore di debug personalizzato, è possibile implementare SP in base alle esigenze del motore di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
