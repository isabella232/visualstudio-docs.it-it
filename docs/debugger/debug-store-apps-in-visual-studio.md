---
title: Debug di App UWP in Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 48a85bcf-290b-4390-9993-f6f9dd73ad03
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 8684a1220b871e2c77f8c0229cddd807a6031cd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debug-uwp-apps-in-visual-studio"></a>Debug di App UWP in Visual Studio
Il debugger di Visual Studio consente di controllare l'esecuzione di un programma e di esaminarne lo stato. È possibile utilizzare il debugger per individuare la causa di errori nelle App UWP e per comprendere esattamente il funzionamento dell'app. Quando sospendi (interrompi) l'esecuzione nel debugger, Visual Studio mostra il file di origine che contiene il codice in esecuzione ed evidenzia l'istruzione in esecuzione. Puoi esaminare i valori delle variabili, lo stack di chiamate delle funzioni in esecuzione e altri aspetti dello stato del programma. Puoi continuare a eseguire (esaminare) il programma un'istruzione alla volta per verificare come le istruzioni cambiano i valori del programma. Nelle app scritte in JavaScript, puoi esaminare e modificare il DOM della pagina.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|||  
|-|-|  
|[Avviare una sessione di debug (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)|Come avviare una sessione di debug: vengono descritte varie opzioni per la configurazione e l'avvio di una sessione di debug per un'app in JavaScript.|  
|[Controllare l'esecuzione in una sessione di debug (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)|L'esplorazione del debugger si basa sull'analisi di una semplice app che dimostra come avviare e arrestare il debug, come spostarsi nel codice e come visualizzare lo stato del programma.|  
|[Guida introduttiva: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)|L'analisi del debug di contenuto HTML e CSS mostra come eseguire in modo interattivo il debug di un'app in JavaScript usando gli strumenti di ispezione DOM attivi per visualizzare e modificare contenuto HTML e CSS.|  
|[Guida introduttiva: Debug di JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)|Debug JavaScript con la console Mostra come eseguire il debug interattivo di un'app in JavaScript usando [comandi della JavaScript Console](../debugger/javascript-console-commands.md).|  
|[Avviare una sessione di debug (VB, c#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)|Come avviare una sessione di debug (Visual C++, Visual C# e Visual Basic): descrive diverse opzioni per la configurazione e l'avvio di una sessione di debug per un'app scritta in Visual C++, Visual C# o Visual Basic.|  
|[Esplorare una sessione di debug (Xaml e c#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)|L'esplorazione del debugger si basa sull'analisi di una semplice app che dimostra come avviare e arrestare il debug, come spostarsi nel codice e come visualizzare e cambiare lo stato del programma.|  
|[Attivare sospensione, ripresa e background eventi per App UWP)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)|Il debugger disabilita gli eventi di gestione del ciclo di vita dei processi Windows che sospendono, riprendono e terminano le app. Puoi attivare questi eventi dalla barra degli strumenti del debugger.<br /><br /> Le attività in background ti permettono di eseguire operazioni importanti anche quando l'app è stata sospesa. Il debugger consente di avviare queste attività in background ed eseguirne il debug.|  
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Presentazione di funzionalità del debugger (in MSDN Library)](http://go.microsoft.com/fwlink/?LinkID=226896)