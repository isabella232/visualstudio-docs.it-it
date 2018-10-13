---
title: IDebugField | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5984e372574ddb104e90415870d3d79020066e3f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218283"
---
# <a name="idebugfield"></a>IDebugField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un campo, vale a dire, una descrizione di un simbolo o del tipo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia come classe base per tutti i campi.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia è la classe base per tutti i campi. In base al valore restituito del [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), questa interfaccia può restituire più specializzate interfacce usando [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). Inoltre, molte delle interfacce restituiscono `IDebugField` oggetti da metodi diversi.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugField`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ottiene visualizzabile informazioni relative al tipo o un simbolo.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ottiene il tipo di campo.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ottiene il tipo di campo.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ottiene il contenitore del campo.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ottiene l'indirizzo del campo.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ottiene le dimensioni di un campo, in byte.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ottiene le informazioni relative a un campo estese.|  
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Confronta due campi.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ottiene indipendenti dal tipo di informazioni sul simbolo o tipo.|  
  
## <a name="remarks"></a>Note  
 Un tipo è equivalente a un linguaggio C `typedef`.  
  
 Nell'esempio seguente del linguaggio C++ `weather` è un tipo di classe, e `sunny` e `stormy` simboli:  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Se un campo rappresenta un simbolo o tipo può essere determinato chiamando [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) ed esaminando il [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) risultato. Se il `FIELD_KIND_TYPE` bit viene impostato, il campo è un tipo e se il `FIELD_KIND_SYMBOL` bit viene impostato, è un simbolo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)

