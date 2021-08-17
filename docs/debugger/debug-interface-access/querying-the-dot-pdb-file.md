---
description: Un file di database di programma (estensione pdb) è un file binario che contiene informazioni di debug di tipo e simboliche raccolte nel corso della compilazione e del collegamento del progetto.
title: Esecuzione di query su . File Pdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 02002589c309bcf4a639af27609e58d9688cb153c564b679b188e0535dd7d720
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379680"
---
# <a name="querying-the-pdb-file"></a>Ricerche nel file PDB
Un file di database di programma (estensione pdb) è un file binario che contiene informazioni di debug di tipo e simboliche raccolte nel corso della compilazione e del collegamento del progetto. Un file PDB viene creato quando si compila un programma C/C++ con **/ZI** o **/Zi** o un programma , o con l'opzione [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] **/debug.** I file oggetto contengono riferimenti al file con estensione pdb per le informazioni di debug. Per altre informazioni sui file pdb, vedere [File PDB](/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). Un'applicazione DIA può usare i passaggi generali seguenti per ottenere informazioni dettagliate sui vari simboli, oggetti ed elementi di dati all'interno di un'immagine eseguibile.

### <a name="to-query-the-pdb-file"></a>Per eseguire query sul file con estensione pdb

1. Acquisire un'origine dati creando [un'interfaccia IDiaDataSource.](../../debugger/debug-interface-access/idiadatasource.md)

    ```C++
    CComPtr<IDiaDataSource> pSource;
    hr = CoCreateInstance( CLSID_DiaSource,
                           NULL,
                           CLSCTX_INPROC_SERVER,
                           __uuidof( IDiaDataSource ),
                          (void **) &pSource);

    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    ```

2. Chiamare [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) o [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) per caricare le informazioni di debug.

    ```C++
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    ```

3. Chiamare [IDiaDataSource::openSession per](../../debugger/debug-interface-access/idiadatasource-opensession.md) aprire [una sessione IDiaSession](../../debugger/debug-interface-access/idiasession.md) per ottenere l'accesso alle informazioni di debug.

    ```C++
    CComPtr<IDiaSession> psession;
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
    ```

4. Usare i metodi in `IDiaSession` per eseguire una query per i simboli nell'origine dati.

    ```C++
    CComPtr<IDiaSymbol> pglobal;
    if ( FAILED( psession->get_globalScope( &pglobal) ) )
    {
        Fatal( "get_globalScope" );
    }
    ```

5. Usare le `IDiaEnum*` interfacce per enumerare ed analizzare i simboli o altri elementi delle informazioni di debug.

    ```C++
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )
    {
        // Do something with each IDiaTable.
    }
    ```

## <a name="see-also"></a>Vedi anche
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
