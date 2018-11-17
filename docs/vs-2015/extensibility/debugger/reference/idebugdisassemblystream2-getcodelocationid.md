---
title: IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs
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
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fbc2890bf91274b825446383d0f1c3e768b315be
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767376"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce un identificatore percorso codice per un contesto di codice specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCodeContext`  
 [in] Un' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto da convertire in un identificatore.  
  
 `puCodeLocationId`  
 [out] Restituisce l'identificatore percorso codice. Vedere la sezione Osservazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_CODE_CONTEXT_OUT_OF_SCOPE` se il contesto del codice è valido, ma all'esterno dell'ambito.  
  
## <a name="remarks"></a>Note  
 L'identificatore percorso codice è specifico per il motore di debug (DE) che supporta il disassembly. Questo identificatore di località viene utilizzato internamente per la Germania per tenere traccia delle posizioni nel codice e in genere è un indirizzo o un offset di qualche tipo. L'unico requisito è che se il contesto del codice di un'unica posizione è inferiore al contesto del codice di un'altra posizione, l'identificatore percorso codice corrispondente del primo contesto di codice deve essere anche minore l'identificatore percorso codice il secondo contesto del codice.  
  
 Per recuperare il contesto del codice di un identificatore percorso codice, chiamare il [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

