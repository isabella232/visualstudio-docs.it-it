---
title: IDebugProgram2::GetName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetName
helpviewer_keywords:
- IDebugProgram2::GetName
ms.assetid: a54cbf13-b3e3-4c9f-8b8d-13573232dfb0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9ec8a234e46fade2b58454d3f4cf8c4ff669564
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917223"
---
# <a name="idebugprogram2getname"></a>IDebugProgram2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il nome del programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrName`  
 [out] Restituisce il nome del programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il nome restituito da questo metodo è sempre un nome descrittivo, visualizzabile dall'utente che descrive il programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
