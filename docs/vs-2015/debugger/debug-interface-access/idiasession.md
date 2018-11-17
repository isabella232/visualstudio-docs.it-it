---
title: IDiaSession | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2baa4b026fd9856625ce25be283c2c969f79a99
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799626"
---
# <a name="idiasession"></a>IDiaSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Fornisce un contesto di query per i simboli di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDiaSession`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Recupera l'indirizzo di caricamento del file eseguibile che corrisponde ai simboli in questo archivio dei simboli. Questo è lo stesso valore passato per il `put_loadAddress` (metodo).|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Imposta l'indirizzo di caricamento del file eseguibile che corrisponde ai simboli in questo archivio dei simboli. **Nota:** è importante chiamare questo metodo quando si riceve un `IDiaSession` dell'oggetto e prima di iniziare a utilizzare l'oggetto.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Recupera un riferimento all'ambito globale.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Recupera un enumeratore per tutte le tabelle incluse nell'archivio simboli.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Recupera un enumeratore per tutti i simboli denominati in posizioni statici.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Recupera tutti gli elementi figlio di un identificatore di oggetto padre specificato che corrispondono al tipo di nome e il simbolo.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Recupera un tipo di simbolo specificato che contiene, o è più vicino, l'indirizzo specificati.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Recupera un tipo di simbolo specificato che contiene, o è più vicino, un indirizzo virtuale relativo specificato (RVA).|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Recupera un tipo di simbolo specificato che contiene, o è più vicino, un indirizzo virtuale specificato (valutazione della vulnerabilità).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Recupera il simbolo che contiene un token di metadati specificato.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Verifica se due simboli sono equivalenti.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Recupera un simbolo mediante il relativo identificatore univoco.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Recupera un tipo di simbolo specificato che contiene, o più vicino a un indirizzo virtuale relativo specificato e l'offset.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Recupera un tipo di simbolo specificato che contiene, o più vicino a un indirizzo virtuale specificato e l'offset.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Recupera un file di origine base compilando e al nome.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Recupera un file di origine dall'identificatore di file di origine.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Recupera i numeri di riga all'interno di un identificatore di file di origine e compilando specificato.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Recupera le righe che contengono un indirizzo specificato in un modulo specificato.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Recupera le righe che contengono un indirizzo virtuale relativo specificato in un modulo specificato.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Consente di trovare le informazioni sul numeri di riga per righe contenute in un intervallo di indirizzi specificato.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Recupera le righe in un modulo specificato dal numero di riga e file di origine.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Recupera un'origine che è stata inserita nell'archivio dei simboli per i provider di attributi o altri componenti del processo di compilazione.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Recupera una sequenza enumerata di flussi di dati di debug.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Recupera un'enumerazione che consente a un client scorrere tutti i frame inline in un determinato indirizzo.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Recupera un'enumerazione che consente a un client scorrere tutti i frame inline in un indirizzo virtuale relativo specificato (RVA).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Recupera un'enumerazione che consente a un client scorrere tutti i frame inline in un indirizzo virtuale specificato (valutazione della vulnerabilità).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Recupera un'enumerazione che consente a un client di eseguire l'iterazione attraverso le informazioni numeriche della riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, dal simbolo del padre specificato.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Recupera un'enumerazione che consente a un client di eseguire l'iterazione attraverso le informazioni numeriche della riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, dal simbolo del padre specificato e è contenuta all'interno dell'intervallo di indirizzi specificato.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Recupera un'enumerazione che consente a un client di eseguire l'iterazione attraverso le informazioni numeriche della riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, dal simbolo del padre specificato e è contenuta all'interno di indirizzo virtuale relativo specificato (RVA).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Recupera un'enumerazione che consente a un client di eseguire l'iterazione attraverso le informazioni numeriche della riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, dal simbolo del padre specificato e è contenuta all'interno dell'indirizzo virtuale specificato (valutazione della vulnerabilità).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Recupera un'enumerazione che consente a un client di eseguire l'iterazione attraverso le informazioni sul numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, il numero di file e righe di origine specificato.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Recupera un'enumerazione che consente a un client di eseguire l'iterazione attraverso le informazioni sul numeri di riga di tutte le funzioni rese inline che corrisponde al nome specificato.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Restituisce un'enumerazione dei simboli per la variabile che il valore di tag specificato corrisponde alla funzione stub tasti di scelta rapida del padre.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Dato un valore di tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in una funzione di stub di tasti di scelta rapida padre specificato in un indirizzo virtuale relativo specificato.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Restituisce un'enumerazione dei simboli per i frame inline corrispondente al nome di funzione inline specificati.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Restituisce un'enumerazione dei simboli per i frame inline che corrispondono al percorso di origine specificato.|  
  
## <a name="remarks"></a>Note  
 È importante chiamare il [Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metodo dopo aver creato il `IDiaSession` oggetto e il valore passato al `put_loadAddress` metodo deve essere diverso da zero, ovvero per tutte le proprietà di indirizzo virtuale (valutazione della vulnerabilità) di simboli a cui essere accessibile. L'indirizzo di caricamento viene fornito da qualsiasi programma caricato il file eseguibile sottoposto a debug. Ad esempio, è possibile chiamare la funzione Win32 `GetModuleInformation` recuperare l'indirizzo di caricamento del file eseguibile, dato un handle al file eseguibile.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come ottenere il `IDiaSession` interfaccia come parte di un'inizializzazione generale di DIA SDK.  
  
```cpp#  
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
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [file exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)



