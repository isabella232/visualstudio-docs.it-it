---
title: Eliminazione di ~ SAK file | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 930ee0690e14431298461f50387a94dd4bb0ce7d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780464"
---
# <a name="elimination-of-sak-files"></a>Eliminazione di file ~SAK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In origine controllo plug-in API 1.2, il ~ SAK file sono stati sostituiti da flag di funzionalità e nuove funzioni che rilevano se un plug-in del controllo del codice sorgente supporta il file MSSCCPRJ estrazioni condivise.  
  
## <a name="sak-files"></a>~ File SAK  
 Visual Studio .NET 2003 creati i file temporanei con preceduti ~ SAK. Questi file vengono usati per determinare se un controllo del codice sorgente del plug-in supporta:  
  
- MSSCCPRJ. File di controllo del codice sorgente.  
  
- Estrazioni multiple (condivise).  
  
  Per i plug-in che supportano funzioni avanzate disponibili nella versione 1.2 API dei plug-in controllo di origine, l'IDE può rilevare queste funzionalità senza creare file temporanei tramite l'uso di nuove funzionalità, flag e le funzioni, dettagliate nelle sezioni seguenti.  
  
## <a name="new-capability-flags"></a>Nuovi flag funzionalità  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Nuove funzioni  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Se un controllo del codice sorgente del plug-in supporta estrazioni multiple (condivise), quindi dichiara il `SCC_CAP_MULTICHECKOUT` capacità e implementa la `SccIsMultiCheckOutEnabled` (funzione). Questa funzione viene chiamata ogni volta che viene eseguita un'operazione di estrazione in uno dei progetti di controllo del codice sorgente.  
  
 Se un controllo del codice sorgente del plug-in supporta la creazione e uso di un MSSCCPRJ. File di controllo del codice sorgente, verrà dichiarata la `SCC_CAP_SCCFILE` capacità e implementa le [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Questa funzione viene chiamata con un elenco di file. La funzione restituisce `TRUE/FALSE` per ogni file indicare se Visual Studio deve utilizzare un MSSCCPRJ. File SCC appositamente. Se il plug-in del controllo del codice sorgente viene scelto di non supportare queste nuove funzionalità e le funzioni, è possibile usare la chiave del Registro di sistema seguente per disabilitare la creazione di questi file:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" runasppl"=DWORD:00000001  
  
> [!NOTE]
>  Se questa chiave del Registro di sistema è impostata su dword:00000000, è equivalente alla chiave in corso inesistenti e Visual Studio continua a tentare di creare i file temporanei. Tuttavia, se la chiave del Registro di sistema è impostata su dword:00000001, Visual Studio non tenta di creare i file temporanei. Invece, si presuppone che il plug-in del controllo del codice sorgente non supporta il MSSCCPRJ. File di controllo del codice sorgente e non supporta estrazioni condivise.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

