---
title: Debug di applicazioni in modalità mista | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
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
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 079ea874e316ede55a489f6f926fd947bd6628fe
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051430"
---
# <a name="debugging-mixed-mode-applications"></a>Debug delle applicazioni in modalità mista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un'applicazione in modalità mista combina codice nativo (C++) con codice gestito, ad esempio Visual Basic, Visual C# o C++ eseguito in Common Language Runtime. Il debug di applicazioni in modalità mista è ampiamente trasparente in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e non è molto diverso dal debug di un'applicazione in modalità singola. È tuttavia necessario fare alcune considerazioni specifiche.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Abilitare la funzione di modifica e continuazione di C++ nel debug in modalità mista  
  
- Per utilizzare Modifica e continuazione per C++ in Visual Studio 2013, è necessario ripristinare il motore di debug legacy. Vedere [Passaggio alla modalità di compatibilità gestita in Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) nel blog Microsoft Application Lifecycle Management.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Valutazione delle proprietà nelle applicazioni in modalità mista  
 In un'applicazione in modalità mista la valutazione delle proprietà tramite il debugger è un'operazione complessa. Di conseguenza, alcune operazioni di debug, ad esempio il debug passo a passo, possono risultare lente. Per altre informazioni, vedere [Esecuzione di un'istruzione del codice alla volta](http://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9). Se nel debug in modalità mista le prestazioni non risultano soddisfacenti, disattivare la valutazione delle proprietà nelle finestre del debugger.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### <a name="to-turn-off-property-evaluation"></a>Per disattivare la valutazione delle proprietà  
  
1. Scegliere **Opzioni** dal menu **Strumenti**.  
  
2. Nella finestra di dialogo **Opzioni** aprire la cartella **Debug** e selezionare la categoria **Generale**.  
  
3. Deselezionare la casella di controllo **Attiva valutazione delle proprietà e altre chiamate di funzioni implicite**.  
  
   Poiché gli stack di chiamate native sono diversi dagli stack di chiamate gestite, il debugger non può sempre fornire lo stack di chiamate completate per il codice misto. Quando il codice nativo chiama il codice gestito, possono essere presenti alcune differenze. Per altre informazioni, vedere [Codice misto e informazioni mancanti nella finestra Stack di chiamate](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)
