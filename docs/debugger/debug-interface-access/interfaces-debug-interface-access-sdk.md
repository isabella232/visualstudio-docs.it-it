---
description: I metodi sono elencati in ordine alfabetico sotto ogni interfaccia nel sommario e nella pagina dell'interfaccia in ordine Vtable.
title: Interfacce (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a225edc9d357f93b76cff7eb4c8c2daef4b4bdda
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065924"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Interfacce (Debug Interface Access SDK)
I metodi sono elencati in ordine alfabetico sotto ogni interfaccia nel sommario e nella pagina dell'interfaccia in ordine Vtable.

## <a name="in-this-section"></a>Contenuto della sezione

[IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)

Fornisce il controllo sul modo in cui il DIA SDK calcola gli indirizzi virtuali virtuali e relativi per gli oggetti di debug.

[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)

Avvia l'accesso a un'origine di simboli di debug.

[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)

Fornisce l'accesso ai record in un flusso di dati di debug.

[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)

Enumera i vari flussi di debug contenuti nell'origine dati.

[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

Enumera i vari elementi dati del frame contenuti nell'origine dati.

[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

Enumerare le varie origini inserite contenute nell'origine dati.

[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

Enumera i vari numeri di riga contenuti nell'origine dati.

[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

Enumera i vari contributi di sezione contenuti nell'origine dati.

[IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

Enumera i vari segmenti contenuti nell'origine dati.

[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

Enumera i vari file di origine contenuti nell'origine dati.

[IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)

Enumera i vari stack frame disponibili.

[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

Enumera i vari simboli contenuti nell'origine dati.

[IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)

Enumera in base all'indirizzo dei vari simboli contenuti nell'origine dati.

[IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)

Enumera le varie tabelle contenute nell'origine dati.

[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

Espone i dettagli di un stack frame.

[IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)

Espone i dettagli della posizione di base e degli offset di memoria del modulo o dell'immagine.

[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

Accede al codice sorgente del programma archiviato nell'origine dati DIA.

[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

Accede alle informazioni che descrivono il processo di mapping da un blocco di byte di testo dell'immagine a un numero di riga del file di origine.

[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)

Riceve callback dalla procedura di individuazione dei simboli DIA, consentendo in tal modo a un'interfaccia utente di segnalare lo stato di avanzamento del tentativo di posizione.

[IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)

Riceve i callback dalla procedura di individuazione dei simboli DIA, consentendo l'imposizione di restrizioni al processo di individuazione.

[IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)

Consente di leggere le proprietà persistenti di un set di proprietà DIA.

[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)

Consente a un'applicazione client di fornire byte di un file eseguibile come specificato dalla posizione del file.

[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)

Consente a un'applicazione client di fornire byte di un file eseguibile come specificato da un indirizzo virtuale relativo.

[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

Recupera i dati che descrivono un contributo di sezione, ad esempio un blocco contiguo di memoria contributo all'immagine da un compilando.

[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

Mappe dati dal numero di sezione ai segmenti dello spazio indirizzi.

[IDiaSession](../../debugger/debug-interface-access/idiasession.md)

Fornisce un contesto di query per i simboli di debug.

[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

Rappresenta un file di origine.

[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)

Espone le proprietà di un oggetto stack frame.

[IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)

Fornisce metodi per eseguire una procedura di analisi dello stack usando il file PDB.

[IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)

Mantiene il contesto dello stack tra le chiamate del [metodo IDiaFrameData::execute.](../../debugger/debug-interface-access/idiaframedata-execute.md)

[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)

Facilita l'analisi dello stack usando il file di database di debug del programma (PDB).

[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

Descrive le proprietà di un'istanza di simbolo.

[IDiaTable](../../debugger/debug-interface-access/idiatable.md)

Enumera una tabella di origine dati DIA.

## <a name="related-sections"></a>Sezioni correlate
[Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)

Vengono descritte le enumerazioni e le strutture utilizzate dalle varie interfacce del DIA SDK.

[Costanti (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)

Descrive le costanti disponibili nel DIA SDK.

## <a name="see-also"></a>Vedi anche

- [Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
