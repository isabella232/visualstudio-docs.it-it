---
title: IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs
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
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d43cf051b90e8a5c0cece3acaf8e1e6ed45b37a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781361"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo recupera l'eccezione associata a un oggetto, se presente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppException`  
 [out] Restituisce l'oggetto che rappresenta l'eccezione.  
  
 `ppField`  
 [out] Restituisce l'oggetto che rappresenta un campo specifico che potrà aver causato l'eccezione (potrebbe trattarsi di un valore null).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
> [!NOTE]
>  Per verificare se si verifica un'eccezione, controllare il valore restituito da `ppException`: se si tratta di un valore null, quindi non è associata a questo oggetto fa eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)

