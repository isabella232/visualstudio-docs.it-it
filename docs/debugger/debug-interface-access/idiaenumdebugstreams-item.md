---
title: IDiaEnumDebugStreams::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Item method
ms.assetid: 6b388fe1-eabc-4720-9d59-dc09b0ceaeac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a07669e36d397550c28d1cc4a5de2ad300763e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744735"
---
# <a name="idiaenumdebugstreamsitem"></a>IDiaEnumDebugStreams::Item
Recupera un flusso di debug per mezzo di un indice o un nome.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item (
    VARIANT                   index,
    IDiaEnumDebugStreamData** stream
);
```

#### <a name="parameters"></a>Parametri
indice

in Indice o nome del flusso di debug da recuperare. Se viene usata una variante Integer, deve essere compresa nell'intervallo da 0 a `count`-1, dove `count` è come restituito dal metodo [IDiaEnumDebugStreams:: get_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md) .

flusso

out Restituisce un oggetto [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) che rappresenta il flusso di debug specificato.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="example"></a>Esempio

```C++
IDiaEnumDebugStreamData *GetStreamData(IDiaEnumDebugStreams *pStreamList,
                                       LONG whichStream)
{
    IDiaEnumDebugStreamData *pStreamData = NULL;
    if (pStreamList != NULL)
    {
        LONG numStreams = 0;
        if (pStreamList->get_count(&numStreams) == S_OK &&
            whichStream >= 0 && whichStream < numStreams)
        {
            VARIANT vIndex;
            vIndex.vt   = VT_I4;
            vIndex.lVal = whichStream;
            if (pStreamList->Item(vIndex,&pStreamData) != S_OK)
            {
                std::cerr << "Error retrieving stream " << whichStream << std::endl;
            }
        }
    }
    return(pStreamData);
}
```

## <a name="see-also"></a>Vedere anche
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
