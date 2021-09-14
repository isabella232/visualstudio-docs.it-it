---
description: Dato un valore tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in questa funzione stub in corrispondenza di un indirizzo virtuale relativo specificato.
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3d1c469d99149bdd21435d7e5b99dd1c193f4659
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626724"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Dato un valore tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in questa funzione stub in corrispondenza di un indirizzo virtuale relativo specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parametri
 `tagValue`

[in] Valore del tag del puntatore per il quale vengono trovati i record del simbolo del puntato.

 `rva`

[in] Oggetto rva usato per filtrare i simboli che corrispondono alla variabile pointee con il valore del tag specificato.

 `ppResult`

[out] Puntatore a un `IDiaEnumSymbols` puntatore a interfaccia inizializzato con il risultato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo solo su `IDiaSymbol` un'interfaccia che corrisponde a una funzione stub dell'acceleratore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
