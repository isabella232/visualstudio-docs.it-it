---
description: Ottiene il nome dell'indicizzatore predefinito.
title: 'IDebugClassField:: GetDefaultIndexer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ebdcab870ba18d38fa6957d37f09abb65db000
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164214"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Ottiene il nome dell'indicizzatore predefinito.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDefaultIndexer( 
   BSTR* pbstrIndexer
);
```

```csharp
int GetDefaultIndexer(
   out string pbstrIndexer
);
```

## <a name="parameters"></a>Parametri
`pbstrIndexer` out Restituisce una stringa contenente il nome dell'indicizzatore predefinito.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non è presente alcun indicizzatore predefinito. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 L'indicizzatore predefinito di una classe è la proprietà contrassegnata come `Default` proprietà per gli accessi alla matrice. Questa operazione è specifica di [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] . Di seguito è riportato un esempio di un indicizzatore predefinito dichiarato in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] e del modo in cui viene usato.

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

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
