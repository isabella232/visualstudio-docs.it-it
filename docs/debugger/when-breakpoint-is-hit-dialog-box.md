---
title: Finestra di dialogo quando il punto di interruzione viene raggiunto | Microsoft Docs
description: Usare quando viene raggiunto il punto di interruzione per specificare un'azione di interruzione. È possibile specificare che un messaggio deve essere stampato e che l'esecuzione debba proseguire in seguito.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bfb5099bd0fab17cd983af4e16a435fd192a1668
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883870"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Finestra di dialogo Quando il punto di interruzione viene raggiunto
Con questa finestra di dialogo è possibile personalizzare l'azione che si verifica quando viene raggiunto un punto di interruzione.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Stampa un messaggio** Stampa un messaggio usando la sintassi DebuggerDisplay. Per ulteriori informazioni, vedere [utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 Questa casella di testo supporta anche parole chiave speciali, ad esempio $ADDRESS, che possono essere usate da soli o tra parentesi graffe di un'espressione DebuggerDisplay. Le parole chiave disponibili sono elencate nella finestra di dialogo.

 **Continua esecuzione** Questo controllo è abilitato solo quando è selezionata **l'opzione stampa un messaggio** . Con questo controllo selezionato, è possibile usare un punto di interruzione come punto di analisi per tracciare l'esecuzione del programma, anziché interferire quando viene raggiunto il percorso.

## <a name="see-also"></a>Vedi anche
- [Utilizzo di punti di interruzione](../debugger/using-breakpoints.md)
- [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)