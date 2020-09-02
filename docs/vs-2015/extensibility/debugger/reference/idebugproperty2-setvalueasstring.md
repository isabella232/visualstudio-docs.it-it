---
title: 'IDebugProperty2:: SetValueAsString | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d50057570b5b067447321f975d4d33da8aa3de43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193434"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Imposta il valore di una proprietà da una stringa specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszValue`  
 in Stringa contenente il valore da impostare.  
  
 `nRadix`  
 in Una radice da usare per interpretare le informazioni numeriche. Questo può essere 0 per tentare di determinare automaticamente la radice.  
  
 `dwTimeout`  
 in Specifica il tempo massimo di attesa, in millisecondi, prima che venga restituito da questo metodo. Usare `INFINITE` per attendere per un periodo illimitato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice errore. Nella tabella seguente vengono illustrati altri valori possibili.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Non è stato possibile convertire la stringa in un valore di proprietà oppure il valore della proprietà non è stato impostato.|  
|`E_SETVALUE_VALUE_IS_READONLY`|la proprietà è di sola lettura.|  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
