---
title: Funzioni di callback implementate dall'IDE | Microsoft Docs
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
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d2bf114a22419e5ed4621db52a68d266e2e7d0e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807534"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funzioni di callback implementate dall'IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per semplificare l'integrazione con l'ambiente di sviluppo integrato (IDE) come facile come possibili e per offrire un'esperienza unificata per l'utente finale, il plug-in del controllo del codice sorgente può usare le funzioni di callback implementate dall'IDE. Il plug-in può chiamare queste funzioni in momenti appropriati durante un'operazione di controllo del codice sorgente per passare le informazioni dell'IDE; l'IDE può quindi visualizzare queste informazioni come gli elementi incorporati nell'interfaccia utente nativa. L'utente ha un'esperienza meno frammentata in questo scenario rispetto a se il plug-in usati la propria interfaccia utente.  
  
 Il file di intestazione obbligatori è scc.h. Il percorso predefinito è \Program Files\VSIP 8.0\EnvSDK\common\inc\\. È anche nella cartella VSIP che include l'esempio di plug-in del controllo di origine a \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>In questa sezione  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Viene descritta la funzione di callback che viene utilizzata dagli [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal controllo del codice sorgente del plug-in tramite l'IDE.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Viene descritta la funzione di callback che viene utilizzata dagli [SccPopulateList](../extensibility/sccpopulatelist-function.md) quando l'IDE non ha accesso completo alle informazioni che sono disponibile solo per il controllo del codice sorgente del plug-in, ad esempio un elenco completo dei file nel controllo della versione.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Viene descritta la funzione di callback che viene usata per il [SccQueryChanges](../extensibility/sccquerychanges-function.md) operazione.  
  
 [POPLISTFUNC](../extensibility/popdirlistfunc.md)  
 Viene descritta la funzione di callback che viene usata per il [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operazione.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Viene descritta la funzione di callback impostata da una chiamata per il [SccSetOption](../extensibility/sccsetoption-function.md) che abilita il controllo del codice sorgente del plug-in per comunicare le modifiche di nome nuovamente l'IDE.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Apre un progetto.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Esamina l'elenco dei file per il relativo stato corrente. Inoltre, utilizza il `pfnPopulate` funzione per notificare al chiamante quando un file non corrisponde ai criteri per il `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Esamina un elenco di directory e file in un progetto o i progetti sottoposti al controllo del codice sorgente. Ogni nome di directory e file trovato viene passato a una funzione di callback.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Esamina modifiche ai nomi che sono state apportate a un elenco di file. Ogni nome di file viene passato a una funzione di callback con lo stato di modifica.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Imposta un'ampia gamma di opzioni. Ogni opzione di avvio con `SCC_OPT_xxx` e ha un proprio set definito di valori.  
  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)  
 Descrive il contenuto della sezione di riferimento del SDK dei plug-in controllo di origine.

