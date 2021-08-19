---
title: Funzioni di callback implementate dall'ide | Microsoft Docs
description: Informazioni sulle funzioni di callback che il plug-in può chiamare nei momenti appropriati durante un'operazione di controllo del codice sorgente per passare informazioni all'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3897c53f186f0e003aa94e9c72ef704b1f8b4e7f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051300"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funzioni di callback implementate dall'IDE
Per semplificare il più possibile l'integrazione con l'ambiente di sviluppo integrato (IDE) e offrire un'esperienza unificata per l'utente finale, il plug-in di controllo del codice sorgente può usare funzioni di callback implementate dall'IDE. Il plug-in può chiamare queste funzioni nei momenti appropriati durante un'operazione di controllo del codice sorgente per passare informazioni all'IDE; L'IDE può quindi visualizzare queste informazioni come elementi incorporati nell'interfaccia utente nativa. L'utente ha un'esperienza meno frammentata in questo scenario rispetto a se il plug-in ha utilizzato la propria interfaccia utente.

 Il file di intestazione richiesto è *scc.h.* Il percorso predefinito è *\Programmi\VSIP 8.0\EnvSDK\common\inc. \\* Si trova anche nella cartella VSIP con l'esempio di plug-in del controllo del codice sorgente in *\Programmi\VSIP 8.0\MSSCCI. \\*

## <a name="in-this-section"></a>Contenuto della sezione
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Descrive la funzione di callback utilizzata da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal plug-in del controllo del codice sorgente tramite l'IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Descrive la funzione di callback utilizzata da [SccPopulateList](../extensibility/sccpopulatelist-function.md) quando l'IDE non ha accesso completo alle informazioni disponibili solo per il plug-in di controllo del codice sorgente, ad esempio un elenco completo di file nel controllo della versione.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Descrive la funzione di callback utilizzata [dall'operazione SccQueryChanges.](../extensibility/sccquerychanges-function.md)

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Descrive la funzione di callback utilizzata [dall'operazione SccPopulateDirList.](../extensibility/sccpopulatedirlist-function.md)

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Descrive la funzione di callback impostata da una chiamata a [SccSetOption](../extensibility/sccsetoption-function.md) che consente al plug-in del controllo del codice sorgente di comunicare le modifiche dei nomi all'IDE.

## <a name="related-sections"></a>Sezioni correlate
- [SccOpenProject](../extensibility/sccopenproject-function.md) Apre un progetto.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Esamina l'elenco dei file per il relativo stato corrente. Usa inoltre la funzione per inviare una notifica al chiamante quando `pfnPopulate` un file non corrisponde ai criteri per `nCommand` .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Esamina un elenco di directory e file in uno o più progetti sotto controllo del codice sorgente. Ogni directory e nome file trovato viene passato a una funzione di callback.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Esamina le modifiche dei nomi apportate a un elenco di file. Ogni nome file viene passato a una funzione di callback insieme al relativo stato di modifica.

- [SccSetOption](../extensibility/sccsetoption-function.md) Imposta un'ampia gamma di opzioni. Ogni opzione inizia con `SCC_OPT_xxx` e ha un proprio set definito di valori.

- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md) Descrive il contenuto della sezione di riferimento dell'SDK del plug-in del controllo del codice sorgente.
