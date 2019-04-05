---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47883395ec12cac60d3a21651432f5ac21cc64a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966792"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Restituisce un'enumerazione dei simboli per i frame inline corrispondente al nome di funzione inline specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `name`  
 [in] Il nome della funzione inline da cercare.  
  
 `option`  
 [in] Le opzioni di ricerca del nome da usare durante la ricerca di inline di fotogrammi che corrispondono a `name`. Per altre informazioni, vedere [enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 [out] Un puntatore a un `IDiaEnumSymbols` puntatore a interfaccia che viene inizializzato con il risultato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questa funzione ricerca inline solo all'interno delle funzioni di stub di tasti di scelta rapida. Ignora i record di procedure native C++.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
