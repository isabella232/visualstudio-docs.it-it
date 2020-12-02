---
title: Eliminazione dei file ~ SAK | Microsoft Docs
description: Informazioni sull'eliminazione dei file ~ SAK dall'API del plug-in del controllo del codice sorgente 1,2 e sul modo in cui sono stati sostituiti dai flag di funzionalità e dalle nuove funzioni.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8e846354b2d48b2f7866daa14987e757f41779c8
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480512"
---
# <a name="elimination-of-sak-files"></a>Eliminazione dei file ~ SAK
Nel plug-in del controllo del codice sorgente API 1,2, i file *~ SAK* sono stati sostituiti dai flag funzionalità e dalle nuove funzioni che rilevano se un plug-in del controllo del codice sorgente supporta il file *Mssccprj* e le estrazioni condivise.

## <a name="sak-files"></a>~ File SAK
Visual Studio .NET 2003 ha creato file temporanei con prefisso *~ SAK*. Questi file vengono usati per determinare se un plug-in del controllo del codice sorgente supporta:

- File *Mssccprj. SCC* .

- Estrazioni multiple (condivise).

Per i plug-in che supportano le funzioni avanzate fornite nell'API del plug-in del controllo del codice sorgente 1,2, l'IDE può rilevare queste funzionalità senza creare i file temporanei tramite l'uso di nuove funzionalità, flag e funzioni, descritti in dettaglio nelle sezioni seguenti.

## <a name="new-capability-flags"></a>Nuovi flag funzionalità
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Nuove funzioni
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Se un plug-in del controllo del codice sorgente supporta più estrazioni (condivise), dichiara la `SCC_CAP_MULTICHECKOUT` funzionalità e implementa la `SccIsMultiCheckOutEnabled` funzione. Questa funzione viene chiamata ogni volta che viene eseguita un'operazione di estrazione in uno dei progetti inclusi nel controllo del codice sorgente.

 Se un plug-in del controllo del codice sorgente supporta la creazione e l'uso di un file *Mssccprj. SCC* , dichiara la `SCC_CAP_SCCFILE` funzionalità e implementa [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Questa funzione viene chiamata con un elenco di file. La funzione restituisce `TRUE' or 'FALSE` per ogni file per indicare se in Visual Studio deve essere utilizzato un file *Mssccprj. SCC* . Se il plug-in del controllo del codice sorgente sceglie di non supportare queste nuove funzionalità e funzioni, può utilizzare la seguente chiave del registro di sistema per disabilitare la creazione di questi file:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]DoNotCreateTemporaryFilesInSourceControl**  =  *DWORD: 00000001*

> [!NOTE]
> Se questa chiave del registro di sistema è impostata su *DWORD: 00000000*, equivale alla chiave inesistente e Visual Studio tenta ancora di creare i file temporanei. Tuttavia, se la chiave del registro di sistema è impostata su *DWORD: 00000001*, Visual Studio non tenta di creare i file temporanei. Si presuppone invece che il plug-in del controllo del codice sorgente non supporti il file *Mssccprj. SCC* e non supporti le estrazioni condivise.

## <a name="see-also"></a>Vedi anche
- [Novità dell'API del plug-in del controllo del codice sorgente versione 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
