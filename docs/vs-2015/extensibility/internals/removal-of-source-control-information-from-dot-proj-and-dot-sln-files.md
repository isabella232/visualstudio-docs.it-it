---
title: Rimozione delle informazioni del controllo del codice sorgente da. Proj e. File sln | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7cdaeb02f77d3775096f840a513f68e531b1299
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199380"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Rimozione delle informazioni del controllo del codice sorgente dai file con estensione proj e sln
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nella versione 1,2 dell'API del plug-in del controllo del codice sorgente le informazioni di SCC sono archiviate in un MSSCCPRJ. File SCC. Il vantaggio del MSSCCPRJ. Il file SCC è che le informazioni di SCC non sono controllate dal codice sorgente, ad esempio nei file. proj e. sln.  
  
## <a name="version-12-changes"></a>Modifiche della versione 1,2  
 Nei plug-in del controllo del codice sorgente basati sull'API del plug-in del controllo del codice sorgente versione 1,1, le informazioni sul controllo del codice sorgente vengono archiviate nei file di progetto (con estensione proj) e di soluzione (con estensione sln). Il percorso del database delle informazioni sul controllo del codice sorgente è specificato da AuxPath e il percorso specifico all'interno del database è specificato da ProjName. Questo comportamento può causare problemi dopo le operazioni di Branch, fork o copia, perché ProjName in genere non è valido dopo una di queste operazioni.  
  
 Nell'API del plug-in del controllo del codice sorgente versione 1,1, l'IDE usava ~ file SAK per rilevare se un plug-in supporta MSSCCPRJ. Metodo SCC per archiviare le informazioni sul controllo del codice sorgente. L'API del plug-in del controllo del codice sorgente versione 1,2 fornisce una nuova funzionalità per il rilevamento del supporto per MSSCCPRJ. File SCC senza usare un file ~ SAK. Per altre informazioni, vedere [eliminazione dei file ~ SAK](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
