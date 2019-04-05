---
title: Getting Started with the Debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d30c45c0601b6e291604275fdc9cfc4f3b5def6d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964340"
---
# <a name="getting-started-with-the-debugger"></a>Introduzione al debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debugger di Visual Studio è facile da utilizzare in qualsiasi linguaggio. Di seguito viene illustrato come eseguire il debug di un semplice programma C#, ma è possibile applicare gli stessi passaggi al codice in altri linguaggi come C++ e JavaScript.  
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> Eseguire il debug di un progetto c# di base  
 Si inizierà con una semplice applicazione console c# (**File / nuovo / progetto**, quindi selezionare **Visual c#** e quindi selezionare **applicazione Console**). Se non si è mai lavorato con Visual Studio in precedenza, vedere [procedura dettagliata: Creare una semplice applicazione](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). Il **Main** metodo semplicemente aggiunge 1 a una variabile integer 10 volte e stampa il risultato nella console:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Compilare questo codice **Debug** configurazione. La configurazione è impostata per impostazione predefinita. Per altre informazioni sulle configurazioni, vedere [informazioni sulle configurazioni della Build](../ide/understanding-build-configurations.md).  
  
 Eseguire questo codice nel debugger facendo **Debug / Avvia debug** (o **avviare** sulla barra degli strumenti, oppure **F5**). L’applicazione si chiude quasi immediatamente, pertanto non è possibile affermare se nella finestra della console è stato stampato qualcosa.  
  
 È possibile interrompere l’esecuzione per un tempo sufficiente a visualizzare la finestra Console impostando un punto di interruzione e quindi procedendo. Per impostare un punto di interruzione, posizionare il cursore del `Console.WriteLine` riga e fare clic su **Debug / nuovo punto di interruzione / punto di interruzione di funzione**, oppure fare semplicemente clic nel margine sinistro della stessa riga. Il punto di interruzione apparirà come segue:  
  
 ![Impostare un punto di interruzione](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Per altre informazioni sui punti di interruzione, vedere [Using Breakpoints](../debugger/using-breakpoints.md).  
  
##  <a name="BKMK_Inspect_Variables"></a> Esaminare le variabili  
 Debug spesso implica la ricerca delle variabili che non contengono i valori che previsti in un momento specifico. Verranno illustrati alcuni dei metodi che è possibile esaminare le variabili.  
  
 Avviare di nuovo il debug. L’esecuzione si interrompe prima dell’esecuzione del codice `Console.WriteLine`. È possibile che vengano esecuzione procedendo (fare clic su **Debug / Step Over** oppure **F10**). In questo caso è possibile scegliere **Esegui istruzione** (**F11**) si otterrebbe lo stesso risultato; è la differenza sarà spiegata più avanti. La riga con l’ultima parentesi graffa del metodo dovrebbe essere diventata gialla. Esaminare la finestra Console. Si noterà **10**.  
  
 È possibile passare il mouse tramite il **testInt** variabile per visualizzare il valore corrente in un suggerimento dati.  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Sotto la finestra del codice dovrebbero vedere le **Auto**, **variabili locali**, e **Watch** windows. Tali finestre mostrano i valori correnti delle variabili al momento dell’esecuzione. Entrambi i **Auto** e il **variabili locali** windows show **testInt** con il valore **10**.  
  
 ![Finestra Auto durante il debug](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Per altre informazioni su queste finestre, vedere [Auto e variabili locali Windows](../debugger/autos-and-locals-windows.md).  
  
 Notare  come cambia il valore di una variabile mentre si esegue il programma. Impostare un punto di interruzione il `testInt += 1;` linea e riavviare il debug. Si noterà che **testInt** nel **variabili locali** e **Auto** windows è **0**, e **ho** è **1**. Se si continua il debug (**Debug / continua**, o **continua** sulla barra degli strumenti, oppure **F5**), è possibile notare che il valore di **testInt** diventa **1**, quindi **2**e così via. Dopo aver verificato di tali modifiche, rimuovere il punto di interruzione (**Debug / Attiva/Disattiva punto di interruzione**, oppure fare clic su di esso nel margine) e continuare il debug. Se si desidera rimuovere tutti i punti di interruzione, fare clic su **Debug / Elimina tutti i punti di interruzione**, o **CTRL + MAIUSC + F9**, fare clic su **Sì** nella finestra di dialogo che chiede **si Se si desidera rimuovere tutti i punti di interruzione?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Step Into e Step Over nelle chiamate di funzione  
 È possibile eseguire codice nel debugger da-istruzione (**Esegui istruzione**) oppure è possibile eseguire codice quando il debugger ignora le funzioni (**Esegui istruzione/routine**) per ottenere rapidamente al codice che si è più interessati ( codice della funzione viene comunque eseguito). È possibile passare tra entrambi i metodi nella stessa sessione di debug.  
  
 Per visualizzare la differenza tra **Esegui istruzione** e **Esegui istruzione/routine**, è necessario aggiungere un metodo che viene chiamato da un altro metodo. Aggiungere un metodo all’applicazione C# e chiamarlo dal metodo Main. Il codice dovrebbe apparire come segue:  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Impostare un punto di interruzione nella chiamata `Method1();` nel metodo Main e avviare il debug. Quando si interrompe l'esecuzione, fare clic su **Debug / Step Into** (o **Esegui istruzione** sulla barra degli strumenti, oppure **F11**). L’esecuzione di interrompe di nuovo alla prima parentesi graffa in Method1():  
  
 ![L'esecuzione di codice](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Arrestare il debug e avviare di nuovo quando l'esecuzione si interrompe al punto di interruzione, fare clic su **Debug / Step Over** (o **Esegui istruzione/routine** sulla barra degli strumenti, oppure **F10**). L'esecuzione si interrompe nuovamente in `Console.WriteLine("end");`.  
  
 Se si desidera saperne di più sull'esplorazione del codice con il debugger, vedere [spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md).
