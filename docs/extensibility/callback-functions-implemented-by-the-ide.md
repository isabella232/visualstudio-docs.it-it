---
title: Funzioni di callback implementate dall'IDE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 666486f5b800707a4467a129abeed7a13306f10a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739899"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Callback functions implemented by the IDE
Per rendere l'integrazione con l'ambiente di sviluppo integrato (IDE) il più semplice possibile e per fornire un'esperienza unificata per l'utente finale, il plug-in del controllo del codice sorgente può utilizzare le funzioni di callback implementate dall'IDE. Il plug-in può chiamare queste funzioni in momenti appropriati durante un'operazione di controllo del codice sorgente per passare informazioni all'IDE; l'IDE può quindi visualizzare queste informazioni come elementi incorporati nell'interfaccia utente nativa. L'utente ha un'esperienza meno frammentata in questo scenario che se il plug-in utilizzato la propria interfaccia utente.

 Il file di intestazione richiesto è *scc.h*. Il percorso predefinito è *.\\* Si trova anche nella cartella VSIP che contiene l'esempio del plug-in del controllo del codice sorgente in *.\\*

## <a name="in-this-section"></a>Contenuto della sezione
- [LPTEXTOUTPROC (LAPTEXTOUTPROC)](../extensibility/lptextoutproc.md) Viene descritta la funzione di callback utilizzata da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal plug-in del controllo del codice sorgente tramite l'IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Viene descritta la funzione di callback utilizzata da [SccPopulateList](../extensibility/sccpopulatelist-function.md) quando l'IDE non dispone dell'accesso completo alle informazioni disponibili solo per il plug-in del controllo del codice sorgente, ad esempio un elenco completo dei file nel controllo della versione.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Descrive la funzione di callback utilizzata dall'operazione [SccQueryChanges.](../extensibility/sccquerychanges-function.md)

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Descrive la funzione di callback utilizzata dall'operazione [SccPopulateDirList.](../extensibility/sccpopulatedirlist-function.md)

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Viene descritta la funzione di callback impostata da una chiamata a [SccSetOption](../extensibility/sccsetoption-function.md) che consente al plug-in del controllo del codice sorgente di comunicare le modifiche del nome all'IDE.

## <a name="related-sections"></a>Sezioni correlate
- [SccOpenProject (progetto SccOpenProject)](../extensibility/sccopenproject-function.md) Apre un progetto.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Esamina l'elenco dei file per il relativo stato corrente. Viene inoltre utilizzata `pfnPopulate` la funzione per notificare al chiamante `nCommand`quando un file non corrisponde ai criteri per il file .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Esamina un elenco di directory e file in un progetto o progetti che si trovano nel controllo del codice sorgente. Ogni directory e nome file trovato viene passato a una funzione di callback.

- [SccQueryChangesSccQueryChanges](../extensibility/sccquerychanges-function.md) Esamina le modifiche al nome apportate a un elenco di file. Ogni nome di file viene passato a una funzione di callback con il relativo stato di modifica.

- [SccSetOption (opzione SccSetOption)](../extensibility/sccsetoption-function.md) Imposta un'ampia gamma di opzioni. Ogni opzione `SCC_OPT_xxx` inizia con e ha un proprio set definito di valori.

- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md) Descrive il contenuto della sezione di riferimento di SDK del plug-in del controllo del codice sorgente.
