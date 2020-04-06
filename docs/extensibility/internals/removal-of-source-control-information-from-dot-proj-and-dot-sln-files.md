---
title: Rimuovere le informazioni sul controllo del codice sorgente dai file con estensione proj e sln
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
ms.openlocfilehash: ba3085a7806bfb0556613d1fca1b94953dcdb0b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705592"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Rimozione delle informazioni del controllo del codice sorgente dai file con estensione proj e sln
Nella versione 1.2 dell'API del plug-in del controllo del codice sorgente le informazioni SCC vengono archiviate in un MSSCCPRJ. file SCC. Il vantaggio di MSSCCPRJ. File SCC è che le informazioni SCC non è origine-controllato, come è nei file .proj e .sln.

## <a name="version-12-changes"></a>Modifiche alla versione 1.2
 Nei plug-in del controllo del codice sorgente basati sull'API del plug-in del controllo del codice sorgente versione 1.1, le informazioni sul controllo del codice sorgente vengono archiviate nei file di progetto (proj) e di soluzione (sln). Il percorso del database delle informazioni sul controllo del codice sorgente è specificato da AuxPath e il percorso specifico all'interno del database è specificato da ProjName. Questo comportamento può causare problemi dopo le operazioni di diramazione, fork o copia perché il ProjName sarebbe in genere non valido dopo una di queste operazioni.

 Nell'API del plug-in del controllo del codice sorgente versione 1.1, l'IDE ha utilizzato i file SAK per rilevare se un plug-in supportava MSSCCPRJ. Metodo SCC per l'archiviazione delle informazioni sul controllo del codice sorgente. L'API plug-in del controllo del codice sorgente versione 1.2 fornisce una nuova funzionalità per il rilevamento del supporto per MSSCCPRJ. SCC senza utilizzare un file sak. Per ulteriori informazioni, vedere [Eliminazione dei file SAK](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Vedere anche
- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
