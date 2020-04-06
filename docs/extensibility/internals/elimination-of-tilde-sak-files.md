---
title: Eliminazione dei file SAK Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708497"
---
# <a name="elimination-of-sak-files"></a>Eliminazione dei file SAK
Nell'API del plug-in del controllo del codice sorgente 1.2, i file di controllo *del codice* sorgente 1.2, i file SAK sono stati sostituiti da flag di funzionalità e nuove funzioni che rilevano se un plug-in del controllo del codice sorgente supporta il file *MSSCCPRJ* e le estrazioni condivise.

## <a name="sak-files"></a>File SAK
Visual Studio .NET 2003 ha creato i file temporanei preceduti da *SAK*. Questi file vengono utilizzati per determinare se un plug-in del controllo del codice sorgente supporta:These files are used to determine if a source control plug-in supports:

- Il file *MSSCCPRJ.SCC.*

- Più estrazioni (condivise).

Per i plug-in che supportano funzioni avanzate disponibili nell'API del plug-in del controllo del codice sorgente 1.2, l'IDE è in grado di rilevare queste funzionalità senza creare i file temporanei tramite l'uso di nuove funzionalità, flag e funzioni, descritte in dettaglio nelle sezioni seguenti.

## <a name="new-capability-flags"></a>Nuovi flag di funzionalità
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Nuove funzioni
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Se un plug-in del controllo del codice sorgente supporta più `SCC_CAP_MULTICHECKOUT` estrazioni `SccIsMultiCheckOutEnabled` (condivise), dichiara la funzionalità e implementa la funzione. Questa funzione viene chiamata ogni volta che si verifica un'operazione di estrazione in uno qualsiasi dei progetti controllati dal codice sorgente.

 Se un plug-in del controllo del codice sorgente supporta la creazione e l'utilizzo `SCC_CAP_SCCFILE` di un file *MSSCCPRJ.SCC,* dichiara la funzionalità e implementa [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Questa funzione viene chiamata con un elenco di file. La funzione `TRUE' or 'FALSE` restituisce per ogni file per indicare se Visual Studio deve utilizzare un file *MSSCCPRJ.SCC* per esso. Se il plug-in del controllo del codice sorgente sceglie di non supportare queste nuove funzionalità e funzioni, è possibile utilizzare la seguente chiave del Registro di sistema per disattivare la creazione di questi file:

 **[HKEY_CURRENT_USER Software Microsoft VisualStudio 8.0/SourceControl] DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
> Se questa chiave del Registro di sistema è impostata su *dword:00000000*, equivale all'inesistente della chiave e Visual Studio tenta comunque di creare i file temporanei. Tuttavia, se la chiave del Registro di sistema è impostata su *dword:00000001*, Visual Studio non tenta di creare i file temporanei. Si presuppone invece che il plug-in del controllo del codice sorgente non supporti il file *MSSCCPRJ.SCC* e non supporti le estrazioni condivise.

## <a name="see-also"></a>Vedere anche
- [Novità dell'API del plug-in del controllo del codice sorgente versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
