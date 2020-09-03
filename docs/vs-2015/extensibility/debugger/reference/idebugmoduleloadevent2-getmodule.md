---
title: 'IDebugModuleLoadEvent2:: GetModule | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0083946051fe78fc1bd19ea877475465e0b6477f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163423"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il modulo che viene caricato o scaricato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pModule`  
 out Restituisce un oggetto [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) che rappresenta il modulo che sta caricando o scaricando.  
  
 `pbstrDebugMessage`  
 [in, out] Restituisce un messaggio facoltativo che descrive questo evento. Se questo parametro è un valore null, non viene richiesto alcun messaggio.  
  
 `pbLoad`  
 [in, out] Diverso da zero ( `TRUE` ) se il modulo viene caricato e zero ( `FALSE` ) se il modulo sta scaricando. Se questo parametro è un valore null, non viene richiesto alcuno stato.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
