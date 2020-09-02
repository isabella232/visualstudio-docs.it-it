---
title: IDebugProgramNameChangedEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: abb117d9de09c11bbce1e1c935e108ec940e9c60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703582"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Inviato dal motore di debug (DE) a gestione debug sessione (SDM) quando viene modificato il nome di un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il DE implementa questa interfaccia per segnalare che il nome del programma è stato modificato. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM utilizza [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) per accedere all'interfaccia **IDebugEvent2** .  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Il DE crea e invia questo oggetto evento per segnalare la modifica di un nome di programma. Il DE Invia questo evento usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug. Il fornitore della porta personalizzata invia questo evento usando l'interfaccia i.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
