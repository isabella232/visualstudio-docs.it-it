---
title: Controllo di esecuzione e valutazione dello stato | Microsoft Docs
description: Informazioni su Visual Studio debug basa il controllo di esecuzione sugli eventi inviati tra i componenti del debugger.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3923976619af3d1b31836663e7137f85be38feefec1aa79271f094244d4d289b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378191"
---
# <a name="execution-control-and-state-evaluation"></a>Controllo di esecuzione e valutazione dello stato
Il debug di un'applicazione richiede l'implementazione di tali funzionalità di controllo dell'esecuzione, ad esempio l'esecuzione di istruzioni nelle funzioni, l'arresto in corrispondenza dei punti di interruzione e la continuazione dell'esecuzione. Visual Studio debug basa il controllo di esecuzione sugli eventi inviati tra i componenti del debugger.

## <a name="in-this-section"></a>Contenuto della sezione
 [Controllo del programma](../../extensibility/debugger/program-control.md) Elenca le routine seguenti che si verificano a livello di programma: impostazione dell'istruzione successiva, esecuzione, esecuzione di istruzioni, continuazione, sospensione e ripresa.

 [Metodi correlati ai punti di interruzione](../../extensibility/debugger/breakpoint-related-methods.md) Definisce i tipi di punti di interruzione associati e in sospeso Visual Studio supportati.

 [Valutazione dello stack di chiamate](../../extensibility/debugger/call-stack-evaluation.md) Viene illustrata l'implementazione dei metodi che consentono la visualizzazione degli stack frame dello stack di chiamate durante la modalità di interruzione.

 [Valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Illustra il modo in cui il motore di debug, la valutazione delle espressioni (edizione Enterprise) e la gestione del debug di sessione sono coinvolti nell'analisi e nella valutazione di un'espressione immessa in una delle finestre dell'IDE.

 [Eventi di controllo](../../extensibility/debugger/control-events.md) Viene illustrata l'interfaccia utilizzata per inviare eventi durante l'esecuzione controllata del programma.
