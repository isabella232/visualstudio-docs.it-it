---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cd6afb417de4d8a362916f91593d0d0e67d307c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156508"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un documento di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] in genere implementa questa interfaccia. Un motore di debug (DE) possa anche implementare questa interfaccia quando è necessario fornire il codice sorgente e l'origine non esiste sul disco.  In questi casi, è necessario implementare anche la Germania [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) e [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) interfacce, nonché su altri metodi di [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) e [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) interfacce.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 I metodi sul `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, e `IDebugActivateDocumentEvent2` interfacce restituiscono questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugDocument2`.  
  
|Metodo|DESCRIZIONE|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Ottiene il nome del documento in uno dei diversi formati.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Ottiene l'identificatore di classe del documento.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia è implementata solo quando la Germania fornisce il codice sorgente. Ad esempio, quando si esegue il debug dello script in una pagina HTML, la Germania fornisce il codice sorgente perché l'origine è scaricato oppure generato in modo dinamico e non esiste come file di disco. Durante il debug tradizionali linguaggi, ad esempio C++, questa interfaccia non devono essere implementati.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
