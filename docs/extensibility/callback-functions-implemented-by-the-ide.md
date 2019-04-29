---
title: Funzioni di callback implementate dall'IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc3b4423b54975c773de743b093f882f1fd9c42c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926936"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funzioni di callback implementate dall'IDE
Per semplificare l'integrazione con l'ambiente di sviluppo integrato (IDE) come facile come possibili e per offrire un'esperienza unificata per l'utente finale, il plug-in del controllo del codice sorgente può usare le funzioni di callback implementate dall'IDE. Il plug-in può chiamare queste funzioni in momenti appropriati durante un'operazione di controllo del codice sorgente per passare le informazioni dell'IDE; l'IDE può quindi visualizzare queste informazioni come gli elementi incorporati nell'interfaccia utente nativa. L'utente ha un'esperienza meno frammentata in questo scenario rispetto a se il plug-in usati la propria interfaccia utente.

 Il file di intestazione obbligatori *scc.h*. Il percorso predefinito è *\Program Files\VSIP 8.0\EnvSDK\common\inc\\*. È anche nella cartella con l'esempio di plug-in del controllo origine all'indirizzo VSIP *\Program Files\VSIP 8.0\MSSCCI\\*.

## <a name="in-this-section"></a>Contenuto della sezione
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) viene descritta la funzione di callback usato da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal controllo del codice sorgente del plug-in tramite l'IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) viene descritta la funzione di callback usato da [SccPopulateList](../extensibility/sccpopulatelist-function.md) quando l'IDE non dispone di accesso completo alle informazioni che sono disponibile solo per il controllo del codice sorgente del plug-in, ad esempio un elenco completo di file nel controllo della versione.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) viene descritta la funzione di callback che viene usata per il [SccQueryChanges](../extensibility/sccquerychanges-function.md) operazione.

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) viene descritta la funzione di callback che viene usata per il [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operazione.

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) viene descritta la funzione di callback impostata da una chiamata per il [SccSetOption](../extensibility/sccsetoption-function.md) che abilita il controllo del codice sorgente del plug-in per comunicare le modifiche di nome nuovamente l'IDE.

## <a name="related-sections"></a>Sezioni correlate
- [SccOpenProject](../extensibility/sccopenproject-function.md) apre un progetto.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) esamina l'elenco dei file per il relativo stato corrente. Inoltre, utilizza il `pfnPopulate` funzione per notificare al chiamante quando un file non corrisponde ai criteri per il `nCommand`.

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) esamina un elenco di directory e file in un progetto o i progetti sottoposti al controllo del codice sorgente. Ogni nome di directory e file trovato viene passato a una funzione di callback.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) esamina modifiche ai nomi che sono state apportate a un elenco di file. Ogni nome di file viene passato a una funzione di callback con lo stato di modifica.

- [SccSetOption](../extensibility/sccsetoption-function.md) imposta un'ampia gamma di opzioni. Ogni opzione di avvio con `SCC_OPT_xxx` e ha un proprio set definito di valori.

- [Plug-in del controllo di origine](../extensibility/source-control-plug-ins.md) descrive il contenuto della sezione di riferimento del SDK dei plug-in controllo di origine.