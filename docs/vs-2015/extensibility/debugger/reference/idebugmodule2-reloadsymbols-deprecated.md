---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs
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
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53dfbc71239eacba447a36cf95430e5c5da461a8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214422"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

OBSOLETE. NON USARE. Ricarica i simboli per questo modulo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszUrlToSymbols`  
 [in] Il percorso dell'archivio simboli.  
  
 `pbstrDebugMessage`  
 [out] Restituisce un messaggio informativo, ad esempio un messaggio di stato o di errore, che viene visualizzato a destra del nome del modulo nella finestra di moduli.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Un motore di debug deve sempre restituire `E_FAIL`.  
  
## <a name="remarks"></a>Note  
 Questo metodo non è più supportato. Implementare il [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) metodo invece.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)

