---
title: Gestione debug sessione | Microsoft Docs
description: Informazioni sulla gestione del debug di sessione, che gestisce più motori di debug per il debug di programmi in più processi in un numero qualsiasi di computer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3ecfcf276339a54c4c77157101b03b9297d54512
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626436"
---
# <a name="session-debug-manager"></a>Gestione debug sessione
Gestione debug sessione (SDM) gestisce un numero qualsiasi di motori di debug (DE) che ese tracciano un numero qualsiasi di programmi in più processi in un numero qualsiasi di computer. Oltre a essere un multiplexer del motore di debug, SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.

## <a name="session-debug-manager-operation"></a>Operazione di gestione del debug di sessione
 Gestione debug sessione (SDM) gestisce il de. In un computer possono essere in esecuzione più motori di debug contemporaneamente. Per eseguire il multiplex delle DE, SDM esegue il wrapping di una serie di interfacce dalle DE ed espone le interfacce all'IDE come singola interfaccia.

 Per migliorare le prestazioni, alcune interfacce non sono multiplexed. Vengono invece usati direttamente dal de e le chiamate a queste interfacce non passano attraverso SDM. Ad esempio, le interfacce usate con la memoria, il codice e i contesti di documento non sono multiplex, perché fanno riferimento a un'istruzione, una memoria o un documento specifico in un programma specifico di cui è stato fatto il debug da un de specifico. Nessun altro DE deve essere coinvolto in questo livello di comunicazione.

 Questo non vale per tutti i contesti. Le chiamate all'interfaccia del contesto di valutazione dell'espressione passano attraverso SDM. Durante la valutazione dell'espressione, SDM esegue il wrapping dell'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) che fornisce all'IDE perché quando tale espressione viene valutata, può coinvolgere più DE che eseguono il debug di programmi nello stesso processo che potrebbero essere in esecuzione nello stesso thread.

 SDM in genere funge da meccanismo di delega, ma può fungere da meccanismo di trasmissione. Ad esempio, durante la valutazione dell'espressione, SDM funge da meccanismo di trasmissione per notificare a tutte le DE che è possibile eseguire codice in un thread specificato. Analogamente, quando il modello SDM riceve un evento di arresto, trasmette ai programmi che devono arrestare l'esecuzione. Quando viene chiamato un passaggio, SDM trasmette ai programmi che possono continuare a eseguire. I punti di interruzione vengono trasmessi anche a ogni de.

 SDM non tiene traccia del programma, del thread o del stack frame. Le informazioni sul processo, sul programma e sul thread vengono inviate a SDM insieme a eventi di debug specifici.

## <a name="see-also"></a>Vedi anche
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
