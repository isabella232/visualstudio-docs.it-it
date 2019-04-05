---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17a6ef52d7df1c60b0cb6581a7e15eeaf67e7875
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969242"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il nome utente dal fornitore della porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrUserName`  
 [out] Stringa contenente il nome utente.  
  
## <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce `S_OK`. In caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 `GetUserName` Restituisce il nome utente visualizzato nei **nome utente** della colonna della **Connetti a processo** nella finestra di dialogo. Per visualizzare il **Connetti a processo** della finestra di dialogo fare clic su **Connetti a processo** sul **strumenti** dal menu il [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
