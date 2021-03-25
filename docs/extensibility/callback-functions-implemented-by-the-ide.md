---
title: Funzioni di callback implementate dall'IDE | Microsoft Docs
description: Informazioni sulle funzioni di callback che il plug-in può chiamare in momenti appropriati durante un'operazione di controllo del codice sorgente per passare informazioni all'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e2e361551fbe03b7f0ef41b19c5d4136aa50472
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068102"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funzioni di callback implementate dall'IDE
Per semplificare il più possibile l'integrazione con il Integrated Development Environment (IDE) e fornire un'esperienza unificata per l'utente finale, il plug-in del controllo del codice sorgente può usare funzioni di callback implementate dall'IDE. Il plug-in può chiamare queste funzioni in momenti appropriati durante un'operazione di controllo del codice sorgente per passare informazioni all'IDE. l'IDE può quindi visualizzare queste informazioni come elementi incorporati nell'interfaccia utente nativa. In questo scenario l'utente ha un'esperienza meno frammentata rispetto al caso in cui il plug-in ha utilizzato una propria interfaccia utente.

 Il file di intestazione richiesto è *SCC. h*. Il percorso predefinito è *\Program Files\VSIP 8.0 \ EnvSDK\common\inc \\*. Si trova anche nella cartella VSIP con l'esempio di plug-in del controllo del codice sorgente in *\Program Files\VSIP 8.0 \\ \ MSSCCI*.

## <a name="in-this-section"></a>Contenuto della sezione
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Viene descritta la funzione di callback utilizzata da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal plug-in del controllo del codice sorgente tramite l'IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Viene descritta la funzione di callback utilizzata da [SccPopulateList](../extensibility/sccpopulatelist-function.md) quando l'IDE non dispone dell'accesso completo alle informazioni disponibili solo per il plug-in del controllo del codice sorgente, ad esempio un elenco completo di file nel controllo della versione.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Descrive la funzione di callback utilizzata dall'operazione [SccQueryChanges](../extensibility/sccquerychanges-function.md) .

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Descrive la funzione di callback utilizzata dall'operazione [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) .

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Viene descritta la funzione di callback impostata da una chiamata a [SccSetOption](../extensibility/sccsetoption-function.md) che consente al plug-in del controllo del codice sorgente di comunicare nuovamente le modifiche del nome all'IDE.

## <a name="related-sections"></a>Sezioni correlate
- [SccOpenProject](../extensibility/sccopenproject-function.md) Apre un progetto.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Esamina l'elenco dei file per il relativo stato corrente. USA inoltre la `pfnPopulate` funzione per notificare al chiamante quando un file non corrisponde ai criteri per l'oggetto `nCommand` .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Esamina un elenco di directory e file in un progetto o in progetti inclusi nel controllo del codice sorgente. Ogni directory e nome file trovati viene passato a una funzione di callback.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Esamina le modifiche dei nomi apportate a un elenco di file. Ogni nome di file viene passato a una funzione di callback insieme al relativo stato di modifica.

- [SccSetOption](../extensibility/sccsetoption-function.md) Imposta un'ampia gamma di opzioni. Ogni opzione inizia con `SCC_OPT_xxx` e ha il proprio set di valori definito.

- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md) Descrive il contenuto della sezione di riferimento dell'SDK del plug-in del controllo del codice sorgente.
