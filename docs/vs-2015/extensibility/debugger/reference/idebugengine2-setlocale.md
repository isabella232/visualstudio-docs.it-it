---
title: IDebugEngine2::SetLocale | Microsoft Docs
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
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8265e9c3b5221448f4bdbeb7f190f7b88f92a07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796857"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Imposta le impostazioni locali del motore di debug (DE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `wLangID`  
 [in] Specifica le impostazioni locali della lingua. Ad esempio, 1033 per inglese.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato dal gestore di sessione di debug (SDM) per la propagazione delle impostazioni locali dell'IDE in modo che le stringhe restituite per la Germania sono localizzate correttamente.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

