---
description: Accede al codice sorgente inserito archiviato nell'origine dati DIA.
title: IDiaInjectedSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource interface
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6b58eae372af82a03dc2629b4b92a5e472342fdd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629729"
---
# <a name="idiainjectedsource"></a>IDiaInjectedSource
Accede al codice sorgente inserito archiviato nell'origine dati DIA.

## <a name="syntax"></a>Sintassi

```
IDiaInjectedSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente vengono illustrati i metodi di `IDiaInjectedSource` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaInjectedSource::get_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|Recupera un controllo di ridondanza ciclico (CRC) calcolato dai byte del codice sorgente.|
|[IDiaInjectedSource::get_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|Recupera il numero di byte di codice.|
|[IDiaInjectedSource::get_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|Recupera il nome file per l'origine.|
|[IDiaInjectedSource::get_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|Recupera il nome del file oggetto in cui è stata compilata l'origine.|
|[IDiaInjectedSource::get_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|Recupera il nome assegnato al codice sorgente non file. ad esempio il codice inserito.|
|[IDiaInjectedSource::get_sourceCompression](../../debugger/debug-interface-access/idiainjectedsource-get-sourcecompression.md)|Recupera l'indicatore della compressione di origine utilizzata.|
|[IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|Recupera i byte del codice sorgente.|

## <a name="remarks"></a>Commenti
L'origine inserita è il testo inserito durante la compilazione. Questo non significa il preprocessore `#include` usato in C++.

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando i [metodi IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) o [IDiaEnumInjectedSources::Next.](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) Per un esempio di come ottenere l'interfaccia, vedere l'interfaccia [IDiaEnumInjectedSources.](../../debugger/debug-interface-access/idiaenuminjectedsources.md) `IDiaInjectedSource`

## <a name="example"></a>Esempio
In questo esempio vengono visualizzati i dati disponibili `IDiaInjectedSource` dall'interfaccia . Per un approccio alternativo [all'uso dell'interfaccia IDiaPropertyStorage,](../../debugger/debug-interface-access/idiapropertystorage.md) vedere l'esempio nell'interfaccia [IDiaEnumInjectedSources.](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

```C++
void PrintInjectedSource(IDiaInjectedSource* pSource)
{
    ULONGLONG codeLength      = 0;
    DWORD     crc             = 0;
    DWORD     compressionType = 0;
    BSTR      sourceFilename  = NULL;
    BSTR      objectFilename  = NULL;
    BSTR      virtualFilename = NULL;

    std::cout << "Injected Source:" << std::endl;
    if (pSource != NULL)
    {
        if (pSource->get_crc(&crc) == S_OK &&
            pSource->get_sourceCompression(&compressionType) == S_OK &&
            pSource->get_length(&codeLength) == S_OK)
        {
            wprintf(L"  crc = %lu\n", crc);
            wprintf(L"  code length = %I64u\n",codeLength);
            wprintf(L"  compression type code = %lu\n", compressionType);
        }

        wprintf(L"  source filename: ");
        if (pSource->get_filename(&sourceFilename) == S_OK)
        {
            wprintf(L"%s", sourceFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        wprintf(L"  object filename: ");
        if (pSource->get_filename(&objectFilename) == S_OK)
        {
            wprintf(L"%s", objectFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        wprintf(L"  virtual filename: ");
        if (pSource->get_filename(&virtualFilename) == S_OK)
        {
            wprintf(L"%s", virtualFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        SysFreeString(sourceFilename);
        SysFreeString(objectFilename);
        SysFreeString(virtualFilename);
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: Dia2.h

Libreria: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)
- [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
