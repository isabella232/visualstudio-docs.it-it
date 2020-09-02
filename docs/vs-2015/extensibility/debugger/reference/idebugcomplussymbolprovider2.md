---
title: IDebugComPlusSymbolProvider2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 868528d5fd7d54f0a515a32895646b0cb94b26ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186492"
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Rappresenta un provider di simboli COM+ con metodi specifici del codice gestito ed estende il IDebugComPlusSymbolProvider **IDebugComPlusSymbolProvider**[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider  
```  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi sull'interfaccia [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) , questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|Determina se il metodo specificato dispone di informazioni sulla riga.|  
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Recupera un tipo in base al nome.|  
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|Recupera un tipo in base al relativo token.|  
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|Determina se l'indirizzo di debug specificato è un punto di sequenza.|  
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|Carica i simboli di debug utilizzando il metodo di callback specificato.|  
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|Caricare i simboli di debug da un flusso di dati dato l'oggetto **ICorDebugModule** .|  
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|Carica i simboli di debug in base all'oggetto **ICorDebugModule** .|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
