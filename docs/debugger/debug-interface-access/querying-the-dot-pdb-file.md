---
description: Un file di database di programma (estensione pdb) è un file binario che contiene informazioni di debug simbolico e di tipo raccolte durante la compilazione e il collegamento del progetto.
title: Esecuzione di query su . File PDB | Microsoft Docs
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
ms.openlocfilehash: 4da3527b8f6834a7fb36077e73ec193204803d80
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097628"
---
# <a name="querying-the-pdb-file"></a>Ricerche nel file PDB
Un file di database di programma (estensione pdb) è un file binario che contiene informazioni di debug simbolico e di tipo raccolte durante la compilazione e il collegamento del progetto. Un file PDB viene creato quando si compila un programma C/C++ con **/ZI** o **/Zi** o un programma , o con [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] **l'opzione /debug.** I file oggetto contengono riferimenti al file con estensione pdb per le informazioni di debug. Per altre informazioni sui file pdb, vedere [File PDB.](/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)) Un'applicazione DIA può usare i passaggi generali seguenti per ottenere informazioni dettagliate sui vari simboli, oggetti ed elementi di dati all'interno di un'immagine eseguibile.

### <a name="to-query-the-pdb-file"></a>Per eseguire una query sul file con estensione pdb

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

3. Chiamare [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) per aprire una [sessione IDiaSession](../../debugger/debug-interface-access/idiasession.md) per ottenere l'accesso alle informazioni di debug.

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

5. Utilizzare le `IDiaEnum*` interfacce per enumerare e analizzare i simboli o altri elementi delle informazioni di debug.

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
