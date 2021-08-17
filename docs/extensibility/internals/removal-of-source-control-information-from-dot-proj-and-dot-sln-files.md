---
title: Rimuovere le informazioni sul controllo del codice sorgente dai file con estensione proj e sln
description: Nell'API plug-in del controllo del codice sorgente le informazioni SCC vengono archiviate in MSSCCPRJ. File SCC anziché i file di progetto e di soluzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5a6db057075b57f07a733af146915db92446a077
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062836"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Rimozione delle informazioni sul controllo del codice sorgente dai file con estensione proj e sln

Nella versione 1.2 dell'API plug-in del controllo del codice sorgente le informazioni SCC vengono archiviate in MSSCCPRJ. File SCC. Il vantaggio di MSSCCPRJ. Il file SCC indica che le informazioni SCC non sono controllate dal codice sorgente, come nei file con estensione proj e sln.

## <a name="version-12-changes"></a>Modifiche della versione 1.2

 Nei plug-in del controllo del codice sorgente basati sull'API plug-in del controllo del codice sorgente versione 1.1, le informazioni sul controllo del codice sorgente vengono archiviate nei file di progetto (con estensione proj) e di soluzione (sln). Il percorso del database delle informazioni sul controllo del codice sorgente viene specificato da AuxPath e il percorso specifico all'interno del database viene specificato da ProjName. Questo comportamento può causare problemi dopo operazioni di diramazione, fork o copia perché ProjName non sarebbe in genere valido dopo una di queste operazioni.

 Nell'API plug-in del controllo del codice sorgente versione 1.1, l'IDE usava ~file SAK per rilevare se un plug-in supportava MSSCCPRJ. Metodo SCC per l'archiviazione delle informazioni sul controllo del codice sorgente. L'API plug-in del controllo del codice sorgente versione 1.2 offre una nuova funzionalità per rilevare il supporto per MSSCCPRJ. SCC senza usare un file ~SAK. Per altre informazioni, vedere [Eliminazione di ~file SAK.](../../extensibility/internals/elimination-of-tilde-sak-files.md)

## <a name="see-also"></a>Vedi anche

- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
