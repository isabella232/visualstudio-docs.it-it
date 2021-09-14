---
description: Fornisce un contesto di query per i simboli di debug.
title: IDiaSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 97a1491b524311f8e48a1e59123e2648efa8d6c1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629076"
---
# <a name="idiasession"></a>IDiaSession
Fornisce un contesto di query per i simboli di debug.

## <a name="syntax"></a>Sintassi

```
IDiaSession : IUnknown
```

## <a name="methods"></a>Metodi
Nella tabella seguente vengono illustrati i metodi di `IDiaSession` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Recupera l'indirizzo di caricamento per il file eseguibile che corrisponde ai simboli in questo archivio simboli. Si tratta dello stesso valore passato al `put_loadAddress` metodo .|
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Imposta l'indirizzo di caricamento per il file eseguibile che corrisponde ai simboli in questo archivio simboli. **Nota:**  È importante chiamare questo metodo quando si ottiene un oggetto e `IDiaSession` prima di iniziare a usare l'oggetto .|
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Recupera un riferimento all'ambito globale.|
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Recupera un enumeratore per tutte le tabelle contenute nell'archivio dei simboli.|
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Recupera un enumeratore per tutti i simboli denominati in posizioni statiche.|
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Recupera tutti gli elementi figlio di un identificatore padre specificato che corrispondono al nome e al tipo di simbolo.|
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Recupera un tipo di simbolo specificato che contiene o è più vicino a un indirizzo specificato.|
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Recupera un tipo di simbolo specificato che contiene o è più vicino a un indirizzo RVA (Relative Virtual Address) specificato.|
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Recupera un tipo di simbolo specificato che contiene o è più vicino a un indirizzo virtuale specificato.|
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Recupera il simbolo che contiene un token di metadati specificato.|
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Verifica se due simboli sono equivalenti.|
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Recupera un simbolo in base al relativo identificatore univoco.|
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Recupera un tipo di simbolo specificato che contiene o è più vicino a un indirizzo virtuale e a un offset relativi specificati.|
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Recupera un tipo di simbolo specificato che contiene o è più vicino a un indirizzo virtuale e a un offset specificati.|
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Recupera un file di origine in base a compilazione e nome.|
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Recupera un file di origine in base all'identificatore del file di origine.|
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Recupera i numeri di riga all'interno di un file di compilazione e di un identificatore di file di origine specificati.|
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Recupera le righe in un compilando specificato che contengono un indirizzo specificato.|
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Recupera le righe in un compilando specificato che contengono un indirizzo virtuale relativo specificato.|
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Trova le informazioni sul numero di riga per le righe contenute in un intervallo di indirizzi specificato.|
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Recupera le righe in un compilando specificato in base al file di origine e al numero di riga.|
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Recupera un'origine inserita nell'archivio dei simboli dai provider di attributi o da altri componenti del processo di compilazione.|
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Recupera una sequenza enumerata di flussi di dati di debug.|
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Recupera un'enumerazione che consente a un client di scorrere tutti i frame inline in un determinato indirizzo.|
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Recupera un'enumerazione che consente a un client di scorrere tutti i frame inline in un indirizzo RVA (Relative Virtual Address) specificato.|
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Recupera un'enumerazione che consente a un client di scorrere tutti i frame inline in un indirizzo virtuale specificato.|
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline, direttamente o indirettamente, dal simbolo padre specificato.|
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline, direttamente o indirettamente, dal simbolo padre specificato e contenute nell'intervallo di indirizzi specificato.|
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline, direttamente o indirettamente, dal simbolo padre specificato e contenute all'interno dell'indirizzo RVA (Relative Virtual Address) specificato.|
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline, direttamente o indirettamente, dal simbolo padre specificato e contenute all'interno dell'indirizzo virtuale specificato.|
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline, direttamente o indirettamente, nel file di origine e nel numero di riga specificati.|
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline che corrispondono a un nome specificato.|
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Restituisce un'enumerazione di simboli per la variabile a cui corrisponde il valore del tag specificato nella funzione stub Accelerator padre.|
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Dato un valore di tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in una funzione stub Accelerator padre specificata in corrispondenza di un indirizzo virtuale relativo specificato.|
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Restituisce un'enumerazione di simboli per i frame inline corrispondenti al nome di funzione inline specificato.|
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Restituisce un'enumerazione di simboli per i frame inline che corrispondono alla posizione di origine specificata.|

## <a name="remarks"></a>Commenti
È importante chiamare il metodo [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) dopo aver creato l'oggetto e il valore passato al metodo deve essere diverso da zero perché tutte le proprietà degli indirizzi virtuali dei simboli siano `IDiaSession` `put_loadAddress` accessibili. L'indirizzo di caricamento proviene da qualsiasi programma che ha caricato il file eseguibile di cui è in corso il debug. Ad esempio, è possibile chiamare la funzione Win32 per recuperare l'indirizzo di caricamento per l'eseguibile, dato `GetModuleInformation` un handle per l'eseguibile.

## <a name="example"></a>Esempio
In questo esempio viene illustrato come ottenere `IDiaSession` l'interfaccia come parte di un'inizializzazione generale del DIA SDK.

```C++
CComPtr<IDiaDataSource> pSource;
ComPtr<IDiaSession> psession;

void InitializeDIA(const char *szFilename)
{
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,
                                   NULL,
                                   CLSCTX_INPROC_SERVER,
                                   __uuidof( IDiaDataSource ),
                                  (void **) &pSource);
    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename,
              szFilename,
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: Dia2.h

Libreria: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [Overview](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [Exe](../../debugger/debug-interface-access/exe.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
- [Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
