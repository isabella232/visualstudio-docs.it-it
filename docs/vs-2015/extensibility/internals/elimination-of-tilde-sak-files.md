---
title: Eliminazione dei file ~ SAK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 751acf4e5f56b7b477f05ab71571e0becd566649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839440"
---
# <a name="elimination-of-sak-files"></a>Eliminazione di file ~SAK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nel plug-in del controllo del codice sorgente API 1,2, i file ~ SAK sono stati sostituiti dai flag funzionalità e dalle nuove funzioni che rilevano se un plug-in del controllo del codice sorgente supporta il file MSSCCPRJ e le estrazioni condivise.  
  
## <a name="sak-files"></a>~ File SAK  
 Visual Studio .NET 2003 ha creato file temporanei con prefisso ~ SAK. Questi file vengono usati per determinare se un plug-in del controllo del codice sorgente supporta:  
  
- MSSCCPRJ. File SCC.  
  
- Estrazioni multiple (condivise).  
  
  Per i plug-in che supportano le funzioni avanzate fornite nell'API del plug-in del controllo del codice sorgente 1,2, l'IDE può rilevare queste funzionalità senza creare i file temporanei tramite l'uso di nuove funzionalità, flag e funzioni, descritti in dettaglio nelle sezioni seguenti.  
  
## <a name="new-capability-flags"></a>Nuovi flag funzionalità  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Funzioni nuove  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Se un plug-in del controllo del codice sorgente supporta più estrazioni (condivise), dichiara la `SCC_CAP_MULTICHECKOUT` funzionalità e implementa la `SccIsMultiCheckOutEnabled` funzione. Questa funzione viene chiamata ogni volta che viene eseguita un'operazione di estrazione in uno dei progetti inclusi nel controllo del codice sorgente.  
  
 Se un plug-in del controllo del codice sorgente supporta la creazione e l'uso di un MSSCCPRJ. Il file SCC, quindi dichiara la `SCC_CAP_SCCFILE` funzionalità e implementa [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Questa funzione viene chiamata con un elenco di file. La funzione restituisce `TRUE/FALSE` per ogni file per indicare se Visual Studio deve usare un Mssccprj. File SCC. Se il plug-in del controllo del codice sorgente sceglie di non supportare queste nuove funzionalità e funzioni, può utilizzare la seguente chiave del registro di sistema per disabilitare la creazione di questi file:  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = DWORD: 00000001  
  
> [!NOTE]
> Se questa chiave del registro di sistema è impostata su DWORD: 00000000, equivale alla chiave inesistente e Visual Studio tenta ancora di creare i file temporanei. Tuttavia, se la chiave del registro di sistema è impostata su DWORD: 00000001, Visual Studio non tenta di creare i file temporanei. Si presuppone invece che il plug-in del controllo del codice sorgente non supporti MSSCCPRJ. Il file SCC e non supporta le estrazioni condivise.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
