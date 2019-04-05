---
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8178adfc1a54d74d758bcfae8272353d5a0c7bd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970169"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia fornisce diversi metodi per l'accesso ai server di una porta e le funzionalità di notifica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia per rappresentare la porta di debug per l'accesso ai programmi. Un fornitore di porte personalizzato possa anche implementare questa interfaccia se gestisce il debug remoto.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Argomento di metodi sul [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaccia fornisce questa interfaccia. La chiamata [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) in un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia possa anche ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi definiti nel [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ottiene l'interfaccia di notifica di porta da questa porta.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ottiene l'interfaccia per il server che ospita questa porta.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina se questa porta è in esecuzione nel computer locale.|  
  
## <a name="remarks"></a>Note  
 Il nome "`IDebugDefaultPort2`" è un po' impropria poiché non rappresenta una porta predefinita. È possibile chiamare "IDebugPort3."  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
