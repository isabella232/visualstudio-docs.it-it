---
title: Finestra di dialogo Quando viene raggiunto il punto di interruzione | Microsoft Docs
description: Usare Quando il punto di interruzione viene raggiunto per specificare un'azione in caso di interruzione. È possibile specificare che un messaggio deve essere stampato e che l'esecuzione deve continuare in un secondo momento.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 444b9c2860e3e79a5fea5b673b68881a1fec4294
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090109"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Finestra di dialogo Quando il punto di interruzione viene raggiunto
Con questa finestra di dialogo è possibile personalizzare l'azione che si verifica quando viene raggiunto un punto di interruzione.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Stampare un messaggio** Stampa un messaggio usando la sintassi DebuggerDisplay. Per altre informazioni, vedere [Uso dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 Questa casella di testo supporta anche parole chiave speciali (ad esempio $ADDRESS) che possono essere usate da sole o tra parentesi graffe di un'espressione DebuggerDisplay. Le parole chiave disponibili sono elencate nella finestra di dialogo.

 **Continua esecuzione** Questo controllo è abilitato solo quando **è selezionata l'opzione Stampa** un messaggio. Con questo controllo selezionato, è possibile usare un punto di interruzione come punto di traccia per tracciare l'esecuzione del programma, anziché interrompersi quando viene raggiunto il percorso.

## <a name="see-also"></a>Vedi anche
- [Uso di punti di interruzione](../debugger/using-breakpoints.md)
- [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)