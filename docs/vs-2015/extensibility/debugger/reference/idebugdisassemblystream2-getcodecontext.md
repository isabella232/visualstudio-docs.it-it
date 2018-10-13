---
title: IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs
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
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 67186f527d3f2814ed67f5b646fa350e364d4c22
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172016"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce un oggetto di contesto codice corrispondente a un identificatore percorso codice specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```csharp  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `uCodeLocationId`  
 [in] Specifica l'identificatore percorso codice. Vedere la sezione Osservazioni per il [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) metodo per una descrizione di un identificatore percorso codice.  
  
 `ppCodeContext`  
 [out] Restituisce un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto che rappresenta il contesto di codice associato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'identificatore percorso codice può essere restituito da una chiamata al [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) metodo e può essere utilizzato nel [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struttura.  
  
 Per convertire un contesto del codice in un identificatore percorso codice, chiamare il [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)

