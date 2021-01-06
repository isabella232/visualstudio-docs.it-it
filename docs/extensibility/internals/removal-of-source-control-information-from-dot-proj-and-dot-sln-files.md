---
title: Rimuovi le informazioni sul controllo del codice sorgente dai file. proj e. sln
description: Nell'API del plug-in del controllo del codice sorgente le informazioni di SCC sono archiviate in un MSSCCPRJ. File SCC anziché i file di progetto e di soluzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 798179a48c24c61fa40c2519624e22a077003b56
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876961"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Rimozione delle informazioni sul controllo del codice sorgente dai file. proj e. sln

Nella versione 1,2 dell'API del plug-in del controllo del codice sorgente le informazioni di SCC sono archiviate in un MSSCCPRJ. File SCC. Il vantaggio del MSSCCPRJ. Il file SCC è che le informazioni di SCC non sono controllate dal codice sorgente, ad esempio nei file. proj e. sln.

## <a name="version-12-changes"></a>Modifiche della versione 1,2

 Nei plug-in del controllo del codice sorgente basati sull'API del plug-in del controllo del codice sorgente versione 1,1, le informazioni sul controllo del codice sorgente vengono archiviate nei file di progetto (con estensione proj) e di soluzione (con estensione sln). Il percorso del database delle informazioni sul controllo del codice sorgente è specificato da AuxPath e il percorso specifico all'interno del database è specificato da ProjName. Questo comportamento può causare problemi dopo le operazioni di Branch, fork o copia, perché ProjName in genere non è valido dopo una di queste operazioni.

 Nell'API del plug-in del controllo del codice sorgente versione 1,1, l'IDE usava ~ file SAK per rilevare se un plug-in supporta MSSCCPRJ. Metodo SCC per archiviare le informazioni sul controllo del codice sorgente. L'API del plug-in del controllo del codice sorgente versione 1,2 fornisce una nuova funzionalità per il rilevamento del supporto per MSSCCPRJ. File SCC senza usare un file ~ SAK. Per altre informazioni, vedere [eliminazione dei file ~ SAK](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Vedi anche

- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
