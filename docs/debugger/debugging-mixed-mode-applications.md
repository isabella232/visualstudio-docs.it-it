---
title: Debug Mixed-Mode applicazioni | Microsoft Docs
description: Eseguire il debug di un'applicazione in modalità mista, ovvero un'app che combina il codice nativo con il codice gestito eseguito in Common Language Runtime, in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dfe0a77b9ed32be07f02abcc837af8595fcd10fb42b2effb0ccece336b57f566
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404554"
---
# <a name="debugging-mixed-mode-applications"></a>Debug delle applicazioni in modalità mista
Un'applicazione in modalità mista combina codice nativo (C++) con codice gestito, ad esempio Visual Basic, Visual C# o C++ eseguito in Common Language Runtime. Il debug di applicazioni in modalità mista è ampiamente trasparente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e non è molto diverso dal debug di un'applicazione in modalità singola. È tuttavia necessario fare alcune considerazioni specifiche.

## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Abilitare la funzione di modifica e continuazione di C++ nel debug in modalità mista

Per abilitare Modifica e continuazione per C++, vedere Come abilitare e [disabilitare Modifica e continuazione.](../debugger/how-to-enable-and-disable-edit-and-continue.md)

> [!NOTE]
> Per utilizzare Modifica e continuazione per C++ in Visual Studio 2013, è necessario ripristinare il motore di debug legacy. Vedere [Passaggio alla modalità di compatibilità gestita in Visual Studio 2013](https://devblogs.microsoft.com/devops/switching-to-managed-compatibility-mode-in-visual-studio-2013/) nel blog Microsoft Application Lifecycle Management.

## <a name="property-evaluation-in-mixed-mode-applications"></a>Valutazione delle proprietà nelle applicazioni in modalità mista
 In un'applicazione in modalità mista la valutazione delle proprietà tramite il debugger è un'operazione complessa. Di conseguenza, alcune operazioni di debug, ad esempio il debug passo a passo, possono risultare lente. Per altre informazioni, vedere [Esecuzione di un'istruzione del codice alla volta](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)). Se nel debug in modalità mista le prestazioni non risultano soddisfacenti, disattivare la valutazione delle proprietà nelle finestre del debugger.

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

### <a name="to-turn-off-property-evaluation"></a>Per disattivare la valutazione delle proprietà

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Nella finestra di dialogo **Opzioni** aprire la cartella **Debug** e selezionare la categoria **Generale**.

3. Deselezionare la casella di controllo **Attiva valutazione delle proprietà e altre chiamate di funzioni implicite**.

   Poiché gli stack di chiamate native sono diversi dagli stack di chiamate gestite, il debugger non può sempre fornire lo stack di chiamate completate per il codice misto. Quando il codice nativo chiama il codice gestito, possono essere presenti alcune differenze. Per altre informazioni, vedere [Codice misto e informazioni mancanti nella finestra Stack di chiamate](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).

## <a name="see-also"></a>Vedi anche

- [Debug del codice gestito](../debugger/debugging-managed-code.md)