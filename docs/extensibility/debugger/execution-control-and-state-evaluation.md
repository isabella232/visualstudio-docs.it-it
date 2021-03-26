---
title: Controllo di esecuzione e valutazione dello stato | Microsoft Docs
description: Informazioni sul modo in cui il debug di Visual Studio basa il controllo dell'esecuzione sugli eventi inviati tra i componenti del debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 598332ec1e9e1cb270360822ca32792b9a53f5c1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096954"
---
# <a name="execution-control-and-state-evaluation"></a>Controllo di esecuzione e valutazione dello stato
Per eseguire il debug di un'applicazione, è necessario implementare tali funzionalità di controllo dell'esecuzione, ad esempio l'esecuzione di funzioni, l'arresto in corrispondenza dei punti di interruzione Il debug di Visual Studio basa il relativo controllo di esecuzione sugli eventi inviati tra i componenti del debugger.

## <a name="in-this-section"></a>Contenuto della sezione
 [Controllo del programma](../../extensibility/debugger/program-control.md) Elenca le routine seguenti che si verificano a livello di programma: impostazione dell'istruzione successiva, esecuzione, esecuzione, esecuzione, continuazione, sospensione e ripresa.

 [Metodi correlati al punto di interruzione](../../extensibility/debugger/breakpoint-related-methods.md) Definisce i tipi di punti di interruzione associati e in sospeso supportati da Visual Studio.

 [Valutazione dello stack di chiamate](../../extensibility/debugger/call-stack-evaluation.md) Viene illustrata l'implementazione dei metodi che consentono la visualizzazione degli stack frame dello stack di chiamate durante la modalità di rottura.

 [Valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Viene illustrato il modo in cui il motore di debug (DE), l'espressione Evaluation (EE) e la gestione del debug della sessione sono interessati all'analisi e alla valutazione di un'espressione immessa in una delle finestre dell'IDE.

 [Eventi di controllo](../../extensibility/debugger/control-events.md) Viene illustrata l'interfaccia utilizzata per inviare eventi durante l'esecuzione controllata del programma.
