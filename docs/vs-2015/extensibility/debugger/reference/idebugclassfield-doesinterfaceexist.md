---
title: IDebugClassField::DoesInterfaceExist | Microsoft Docs
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
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 941451b281a1f9794282516f9d9212c24e452682
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763480"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se un'interfaccia specifica viene definita nella classe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszInterfaceName`  
 [in] Stringa contenente il nome dell'interfaccia da cercare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK, restituisce S_FALSE se l'interfaccia non esiste. in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In effetti, questo metodo ottiene un'enumerazione di tutte le interfacce e Cerca nell'elenco per un'interfaccia corrisponda.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

