---
title: Rimozione delle informazioni di controllo di origine da. Proj e. File sln | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c6709d7808eba229455805ecb2b4a8d0c8af525
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540452"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Rimozione delle informazioni del controllo del codice sorgente dai file con estensione proj e sln
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [la rimozione di informazioni del controllo sorgente da. Proj e. File sln](https://docs.microsoft.com/visualstudio/extensibility/internals/removal-of-source-control-information-from-dot-proj-and-dot-sln-files).  
  
Nella versione 1.2 dell'API di plug-in del controllo origine controllo configurazione sistema informazioni vengono archiviate in un MSSCCPRJ. File di controllo del codice sorgente. Il vantaggio del MSSCCPRJ. File di controllo del codice sorgente è che le informazioni di controllo del codice sorgente non è origine - controllato, come nel caso in file con estensione proj e sln.  
  
## <a name="version-12-changes"></a>Modifiche della versione 1.2  
 In origine plug-in del controllo che si basano sull'API dei plug-in controllo di origine versione 1.1, informazioni sul controllo del codice sorgente vengono archiviate nei file di soluzione (sln) e del progetto (proj). Il percorso del database delle informazioni di controllo di origine specificato da di AuxPath e la posizione specifica all'interno del database specificata da ProjName. Questo comportamento può causare problemi dopo la diramazione, fork o operazioni di copia perché il ProjName in genere sarebbe più validi dopo una di queste operazioni.  
  
 Nell'API di plug-in del controllo origine versione 1.1, l'IDE utilizzata ~ file SAK per rilevare se un plug-in supportati il MSSCCPRJ. Metodo di controllo del codice sorgente dell'archiviazione delle informazioni di controllo di origine. L'API dei plug-in del controllo origine versione 1.2 fornisce una nuova funzionalità per rilevare il supporto per MSSCCPRJ. File di controllo del codice sorgente senza utilizzare un ~ file SAK. Per altre informazioni, vedere [azzerare ~ SAK file](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

