---
title: Windows Script Host | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows Script Host, implementing hosts
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51053dec1f8362aa9eef80e4867d2f92a06454cb
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835329"
---
# <a name="windows-script-hosts"></a>Windows Script Host
Durante l'implementazione di Microsoft Windows Script host, è possibile tranquillamente presupporre che un motore di scripting chiami solo l'interfaccia [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) nel contesto del thread di base fino a quando l'host esegue le operazioni seguenti:  
  
- Sceglie un thread di base (in genere il thread che contiene il ciclo di messaggi).  
  
- Crea un'istanza del motore di scripting nel thread di base.  
  
- Chiama i metodi del motore di scripting solo dal thread di base, fatto salvo dove è consentito in modo specifico, come nei casi di [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) e [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
- Chiama l'oggetto di distribuzione del motore di scripting solo dal thread di base.  
  
- Assicura che il ciclo di messaggi venga eseguito nel thread di base se viene fornito un punto di controllo della finestra.  
  
- Garantisce che solo gli eventi di origine nel thread di base del modello gli oggetti nell'oggetto dell'host.  
  
  Queste regole sono seguite automaticamente da tutti gli host a thread singolo. Il modello con restrizioni descritto in precedenza è intenzionalmente debole per consentire a un host di interrompere uno script bloccato chiamando [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) da un altro thread (avviato da un gestore di CTRL+INTERR o simili) o per duplicare uno script in un nuovo thread tramite [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## <a name="remarks"></a>Osservazioni  
 Nessuna di queste restrizioni si applica a un host che sceglie di implementare un'interfaccia a thread libero [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) e un modello dell'oggetto a thread libero. Un host simile può usare l'interfaccia [IActiveScript](../winscript/reference/iactivescript.md) da qualsiasi thread, senza alcuna restrizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Windows Script](../winscript/windows-script-interfaces.md)