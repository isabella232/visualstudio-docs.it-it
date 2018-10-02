---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5b7ca39a36bafe2ebba838c7f6d03f89e2f8132
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527281"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProperty3::CreateObjectID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty3-createobjectid).  
  
Crea un ID univoco per questa proprietà per assicurarsi che sia univoco tra tutte le altre proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato quando il gestore di sessione di debug vuole assicurarsi che questa proprietà è identificata in modo univoco tra tutte le altre proprietà. Il motore di debug (DE) supporta questo metodo, a meno che le proprietà che si occupa sono già identificate. Se la Germania non supporta questo metodo, viene restituito `E_NOTIMPL`.  
  
 Qualsiasi ID univoco creato con `CreateObjectID` viene eliminato quando il [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) viene chiamato il metodo; ciò indica anche la fine dell'esigenza di identifica in modo univoco questa proprietà.  
  
> [!NOTE]
>  Non è disponibile alcun metodo per recuperare l'ID univoco, in modo che la Germania è possibile eseguire qualsiasi risultato per ID univoci quando la `CreateObjectID` viene chiamato il metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)

