---
title: IDebugClassField::GetDefaultIndexer | Microsoft Docs
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
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b632103d30dddb178ad0d2866f72e6f864d9f197
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540910"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugClassField::GetDefaultIndexer](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugclassfield-getdefaultindexer).  
  
Ottiene il nome dell'indicizzatore predefinita.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetDefaultIndexer(   
   BSTR* pbstrIndexer  
);  
```  
  
```csharp  
int GetDefaultIndexer(  
   out string pbstrIndexer  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrIndexer`  
 [out] Restituisce una stringa contenente il nome dell'indicizzatore predefinita.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se non esiste alcun indicizzatore predefinito. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'indicizzatore predefinito di una classe è la proprietà che è contrassegnata come il `Default` proprietà per gli accessi alla matrice. Questo è specifico di [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]. Di seguito è riportato un esempio di un indicizzatore predefinito dichiarato in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] e modalità di utilizzo.  
  
```vb  
Imports System.Collections;  
  
Public Class Class1  
    Private myList as Hashtable  
  
    Default Public Property Item(ByVal Index As Integer) As Integer  
        Get  
            Return CType(List(Index), Integer)  
        End Get  
        Set(ByVal Value As Integer)  
            List(Index) = Value  
        End Set  
    End Property  
End Class  
  
Function GetItem(Index as Integer) as Integer  
    Dim classList as Class1 = new Class1  
    Dim value as Integer  
  
    ' Access array through default indexer  
    value = classList(2)  
  
    ' Access array through explicit property  
    value = classList.Item(2)  
  
    Return value  
End Function  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

