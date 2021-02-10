---
title: Gestione debug sessione | Microsoft Docs
description: Informazioni su gestione debug sessione, che consente di gestire più motori di debug programmi di debug in più processi in un numero qualsiasi di computer.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d67716f78249bda5d316ffde175b80f4ef1c1e45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960780"
---
# <a name="session-debug-manager"></a>Gestione debug sessione
Gestione debug sessione (SDM) gestisce un numero qualsiasi di motori di debug (DE) che eseguono il debug di un numero qualsiasi di programmi in più processi in un numero qualsiasi di computer. Oltre a essere un motore di debug multiplexer, SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.

## <a name="session-debug-manager-operation"></a>Operazione di gestione del debug della sessione
 Gestione debug sessione (SDM) gestisce il DE. In un computer può essere in esecuzione contemporaneamente più di un motore di debug. Per eseguire il multiplexing delle DEs, il SDM esegue il wrapping di un numero di interfacce dal DEs e le espone all'IDE come una singola interfaccia.

 Per migliorare le prestazioni, alcune interfacce non vengono multiplexate. Vengono invece utilizzati direttamente da DE e le chiamate a queste interfacce non passano attraverso la SDM. Ad esempio, le interfacce usate con i contesti di memoria, di codice e di documento non vengono sottoposte a multiplexing, perché fanno riferimento a un'istruzione, a una memoria o a un documento specifico in un programma specifico sottoposto a debug da uno specifico DE. Non è necessario che altre richieste siano necessarie per questo livello di comunicazione.

 Questa operazione non è valida per tutti i contesti. Le chiamate all'interfaccia del contesto di valutazione dell'espressione passano attraverso l'SDM. Durante la valutazione dell'espressione, il SDM esegue il wrapping dell'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) che fornisce all'IDE perché, quando tale espressione viene valutata, può coinvolgere più des che eseguono il debug di programmi nello stesso processo che potrebbe essere in esecuzione nello stesso thread.

 Il SDM funge in genere da meccanismo di delega, ma può fungere da meccanismo di trasmissione. Ad esempio, durante la valutazione dell'espressione, SDM funge da meccanismo di trasmissione per notificare a tutti i DEs che possono eseguire codice in un thread specificato. Analogamente, quando SDM riceve un evento di arresto, trasmette ai programmi che dovrebbero arrestare l'esecuzione. Quando viene chiamato un passaggio, l'SDM trasmette ai programmi che possono continuare l'esecuzione. I punti di interruzione vengono trasmessi anche a ogni DE.

 SDM non rileva il programma, il thread o la stack frame corrente. Le informazioni relative al processo, al programma e al thread vengono inviate all'SDM insieme a eventi di debug specifici.

## <a name="see-also"></a>Vedi anche
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
