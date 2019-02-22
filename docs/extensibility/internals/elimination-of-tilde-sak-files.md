---
title: Eliminazione di ~ SAK file | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99d776e7d9891ca231fde4531b558de66568904f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641468"
---
# <a name="elimination-of-sak-files"></a>Eliminazione di ~ file SAK
In origine controllo plug-in API 1.2, il *~ SAK* i file sono stati sostituiti dai flag funzionalità e nuove funzioni di rilevare la presenza di un'origine di controllo del plug-in supporta le *MSSCCPRJ* file ed estrazioni condivise.

## <a name="sak-files"></a>~ File SAK
Visual Studio .NET 2003 creati i file temporanei con preceduti *~ SAK*. Questi file vengono usati per determinare se un controllo del codice sorgente del plug-in supporta:

- Il *Mssccprj. scc* file.

- Estrazioni multiple (condivise).

Per i plug-in che supportano funzioni avanzate disponibili nella versione 1.2 API dei plug-in controllo di origine, l'IDE può rilevare queste funzionalità senza creare file temporanei tramite l'uso di nuove funzionalità, flag e le funzioni, dettagliate nelle sezioni seguenti.

## <a name="new-capability-flags"></a>Nuovi flag funzionalità
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Nuove funzioni
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Se un controllo del codice sorgente del plug-in supporta estrazioni multiple (condivise), quindi dichiara il `SCC_CAP_MULTICHECKOUT` capacità e implementa la `SccIsMultiCheckOutEnabled` (funzione). Questa funzione viene chiamata ogni volta che viene eseguita un'operazione di estrazione in uno dei progetti di controllo del codice sorgente.

 Se un controllo del codice sorgente del plug-in supporta la creazione e uso di un' *Mssccprj. scc* del file, quindi dichiara il `SCC_CAP_SCCFILE` funzionalità e implementa la [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Questa funzione viene chiamata con un elenco di file. La funzione restituisce `TRUE' or 'FALSE` per ogni file indicare se Visual Studio deve utilizzare un *Mssccprj. scc* per tale file. Se il plug-in del controllo del codice sorgente viene scelto di non supportare queste nuove funzionalità e le funzioni, è possibile usare la chiave del Registro di sistema seguente per disabilitare la creazione di questi file:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
>  Se questa chiave del Registro di sistema è impostata su *dword:00000000*è equivalente alla chiave in corso inesistenti e Visual Studio continua a tentare di creare i file temporanei. Tuttavia, se la chiave del Registro di sistema è impostata su *dword:00000001*, Visual Studio non tenta di creare i file temporanei. In alternativa, si presuppone che il plug-in del controllo del codice sorgente non supporta il *Mssccprj. scc* file e non supporta estrazioni condivise.

## <a name="see-also"></a>Vedere anche
- [Novità di plug-in origine controllo API versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)