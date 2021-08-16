---
title: Eliminazione di ~SAK Files | Microsoft Docs
description: Informazioni sull'eliminazione di ~file SAK dall'API plug-in del controllo del codice sorgente 1.2 e su come sono stati sostituiti da flag di funzionalità e nuove funzioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c4fb89b2bb6ab3e895e77257bce83f1308ea73b7ca72209453e2d32f3440c344
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359494"
---
# <a name="elimination-of-sak-files"></a>Eliminazione di ~file SAK
Nell'API plug-in del controllo del codice sorgente 1.2 i *file ~SAK* sono stati sostituiti da flag di funzionalità e nuove funzioni che rilevano se un plug-in di controllo del codice sorgente supporta il file *MSSCCPRJ* e le estrazioni condivise.

## <a name="sak-files"></a>~File SAK
Visual Studio .NET 2003 ha creato file temporanei con prefisso *~SAK.* Questi file vengono usati per determinare se un plug-in del controllo del codice sorgente supporta:

- File *MSSCCPRJ.SCC.*

- Più estrazioni (condivise).

Per i plug-in che supportano le funzioni avanzate fornite nell'API plug-in del controllo del codice sorgente 1.2, l'IDE può rilevare queste funzionalità senza creare i file temporanei tramite l'uso di nuove funzionalità, flag e funzioni, descritte in dettaglio nelle sezioni seguenti.

## <a name="new-capability-flags"></a>Nuovi flag di funzionalità
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Nuove funzioni
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Se un plug-in del controllo del codice sorgente supporta più estrazioni (condivise), dichiara la funzionalità e `SCC_CAP_MULTICHECKOUT` implementa la `SccIsMultiCheckOutEnabled` funzione . Questa funzione viene chiamata ogni volta che si verifica un'operazione di estrazione in uno dei progetti controllati dal codice sorgente.

 Se un plug-in del controllo del codice sorgente supporta la creazione e l'uso di un file *MSSCCPRJ.SCC,* dichiara la funzionalità e implementa `SCC_CAP_SCCFILE` [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Questa funzione viene chiamata con un elenco di file. La funzione restituisce per ogni file per indicare se Visual Studio deve usare un `TRUE' or 'FALSE` file *MSSCCPRJ.SCC.* Se il plug-in del controllo del codice sorgente sceglie di non supportare queste nuove funzionalità e funzioni, può usare la chiave del Registro di sistema seguente per disabilitare la creazione di questi file:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]DoNotCreateTemporaryFilesInSourceControl**  =  *dword:00000001*

> [!NOTE]
> Se questa chiave del Registro di sistema è impostata su *dword:00000000,* equivale alla chiave inesistente e Visual Studio tenta comunque di creare i file temporanei. Tuttavia, se la chiave del Registro di sistema è impostata su *dword:00000001*, Visual Studio non tenta di creare i file temporanei. Presuppone invece che il plug-in del controllo del codice sorgente non supporti il file *MSSCCPRJ.SCC* e non supporti le estrazioni condivise.

## <a name="see-also"></a>Vedi anche
- [Novità dell'API plug-in del controllo del codice sorgente versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
