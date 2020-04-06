---
title: 'Gestione debug sessione : Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953b4e948ef5e21531a3e73bceed3a363ed3cec5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712877"
---
# <a name="session-debug-manager"></a>Gestione debug sessione
Gestione di debug di sessione (SDM) gestisce un numero qualsiasi di motori di debug (DE) che eseguono il debug di un numero qualsiasi di programmi in più processi su un numero qualsiasi di computer. Oltre a essere un multiplexer del motore di debug, il modello SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.

## <a name="session-debug-manager-operation"></a>Operazione del gestore di debug della sessione
 Il gestore di sessione di debug (SDM) gestisce il DE. In un computer possono essere in esecuzione più motori di debug contemporaneamente. Per multiplex dEs, il file SDM esegue il wrapping di un numero di interfacce da dE e li espone all'IDE come un'unica interfaccia.

 Per migliorare le prestazioni, alcune interfacce non sono multiplexed. Al contrario, vengono utilizzati direttamente dal DE e le chiamate a queste interfacce non passano attraverso il sDM. Ad esempio, le interfacce utilizzate con i contesti di memoria, codice e documento non sono multiplexed, perché si riferiscono a un'istruzione specifica, memoria o documento in un programma specifico sottoposto a debug da un DE specifico. Nessun'altra DE deve essere coinvolta in questo livello di comunicazione.

 Questo non vale per tutti i contesti. Le chiamate all'interfaccia del contesto di valutazione dell'espressione passano attraverso il file SDM. Durante la valutazione dell'espressione, il modello SDM esegue il wrapping di [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia che fornisce all'IDE perché quando tale espressione viene valutata, può coinvolgere più DEs che eseguono il debug di programmi nello stesso processo che potrebbe essere in esecuzione sullo stesso thread.

 Il meccanismo DiSM in genere funge da meccanismo di delega, ma potrebbe fungere da meccanismo di trasmissione. Ad esempio, durante la valutazione dell'espressione, il modello SDM funge da meccanismo di trasmissione per notificare a tutti i DE che possono eseguire codice in un thread specificato. Analogamente, quando il modello SDM riceve un evento di arresto, trasmette ai programmi che devono interrompere l'esecuzione. Quando viene chiamato un passaggio, il file SDM trasmette ai programmi che possono continuare a eseguire. I punti di interruzione vengono trasmessi anche a ogni DE.

 Il modello SDM non tiene traccia del programma, del thread o dello stack frame corrente. Le informazioni sul processo, sul programma e sul thread vengono inviate al modello SDM insieme a eventi di debug specifici.

## <a name="see-also"></a>Vedere anche
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
- [Contesti del debuggerDebugger contexts](../../extensibility/debugger/debugger-contexts.md)
