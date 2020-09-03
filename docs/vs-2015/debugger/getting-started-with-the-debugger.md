---
title: Introduzione con il debugger | Microsoft Docs
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
ms.openlocfilehash: e093abd5e836bcb7ee236979c00d574a07ecfd3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202344"
---
# <a name="getting-started-with-the-debugger"></a>Introduzione al debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debugger di Visual Studio è facile da utilizzare in qualsiasi linguaggio. Di seguito viene illustrato come eseguire il debug di un semplice programma C#, ma è possibile applicare gli stessi passaggi al codice in altri linguaggi come C++ e JavaScript.  
  
## <a name="debug-a-basic-c-project"></a><a name="BKMK_Start_debugging_a_VS_project"></a> Eseguire il debug di un progetto C# di base  
 Iniziamo con una semplice applicazione console C# (**file/nuovo/progetto**, quindi seleziona **Visual C#** e quindi seleziona **applicazione console**). Se non si è mai usato Visual Studio prima, vedere [procedura dettagliata: creare un'applicazione semplice](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). Il metodo **Main** aggiunge solo 1 a una variabile Integer 10 volte e stampa il risultato nella console:  
  
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
  
 Compilare questo codice nella configurazione di **debug** . La configurazione è impostata per impostazione predefinita. Per ulteriori informazioni sulle configurazioni, vedere [informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).  
  
 Eseguire questo codice nel debugger facendo clic su **debug/Avvia debug** (oppure **Avvia** sulla barra degli strumenti o **F5**). L’applicazione si chiude quasi immediatamente, pertanto non è possibile affermare se nella finestra della console è stato stampato qualcosa.  
  
 È possibile interrompere l’esecuzione per un tempo sufficiente a visualizzare la finestra Console impostando un punto di interruzione e quindi procedendo. Per impostare un punto di interruzione, posizionare il cursore nella `Console.WriteLine` riga e fare clic su **debug/nuovo**punto di interruzione/punto di interruzione della funzione o fare semplicemente clic sul margine sinistro nella stessa riga. Il punto di interruzione apparirà come segue:  
  
 ![Imposta un punto di interruzione](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Per ulteriori informazioni sui punti di interruzione, vedere Utilizzo di punti di [interruzione](../debugger/using-breakpoints.md).  
  
## <a name="inspect-variables"></a><a name="BKMK_Inspect_Variables"></a> Esaminare le variabili  
 Il debug spesso implica la ricerca di variabili che non contengono i valori previsti in un determinato punto. Vengono illustrati alcuni dei modi in cui è possibile esaminare le variabili.  
  
 Avviare di nuovo il debug. L’esecuzione si interrompe prima dell’esecuzione del codice `Console.WriteLine`. È possibile fare in modo che l'esecuzione venga eseguita facendo avanzare (fare clic su **Debug/Esegui istruzione/** routine o **F10**). In questo caso è possibile avere scelto **Esegui istruzione** (**F11**) e ottenere lo stesso risultato; in seguito verrà illustrata la differenza. La riga con l’ultima parentesi graffa del metodo dovrebbe essere diventata gialla. Esaminare la finestra Console. Dovrebbe essere visualizzato **10**.  
  
 È possibile passare il puntatore del mouse sulla variabile **TestInt** per visualizzare il valore corrente in un suggerimento dati.  
  
 ![DBG&#95;nozioni di base&#95;dati&#95;suggerimenti](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Immediatamente sotto la finestra del codice verranno visualizzate le finestre **auto**, **variabili locali**e **espressioni di controllo** . Tali finestre mostrano i valori correnti delle variabili al momento dell’esecuzione. In entrambe le finestre **auto** e **variabili locali** viene visualizzato **TestInt** con il valore **10**.  
  
 ![Finestra Auto durante il debug](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Per ulteriori informazioni su queste finestre, vedere la pagina relativa alle [finestre auto e variabili locali](../debugger/autos-and-locals-windows.md).  
  
 Notare  come cambia il valore di una variabile mentre si esegue il programma. Impostare un punto di interruzione sulla `testInt += 1;` riga e riavviare il debug. Si noterà che **TestInt** nelle finestre **variabili locali** e **auto** è **0**e **sono** **1**. Quando si continua il debug (**debug/continua**o **continua** sulla barra degli strumenti o **F5**), è possibile notare che il valore di **TestInt** viene modificato in **1**, quindi **2**e così via. Quando si è stanchi di esaminare queste modifiche, rimuovere il punto di interruzione (**debug/Imposta/Rimuovi**punto di interruzione oppure fare clic su di esso nel margine) e continuare il debug. Se si desidera rimuovere tutti i punti di interruzione, fare clic su **debug/Elimina tutti**i punti di interruzione oppure **premere CTRL + MAIUSC + F9**, quindi fare clic su **Sì** nella finestra di dialogo in cui viene chiesto se **si desidera rimuovere tutti i punti di interruzione**.  
  
## <a name="stepping-into-and-over-function-calls"></a>Step Into e Step Over nelle chiamate di funzione  
 È possibile eseguire il codice nell'istruzione-by-Statement del debugger (**Esegui**istruzione) oppure eseguire codice mentre il debugger ignora le funzioni (**Esegui**istruzione/routine) per ottenere rapidamente codice a cui si è maggiormente interessati (il codice della funzione è ancora in esecuzione). È possibile passare da un metodo all'altra nella stessa sessione di debug.  
  
 Per visualizzare la differenza tra **Esegui** istruzione ed **Esegui istruzione**/routine, è necessario aggiungere un metodo chiamato da un altro metodo. Aggiungere un metodo all’applicazione C# e chiamarlo dal metodo Main. Il codice dovrebbe apparire come segue:  
  
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
  
 Impostare un punto di interruzione nella chiamata `Method1();` nel metodo Main e avviare il debug. Quando l'esecuzione si interrompe, fare clic su **Debug/Esegui istruzione** (o **Esegui istruzione** nella barra degli strumenti o **F11**). L’esecuzione di interrompe di nuovo alla prima parentesi graffa in Method1():  
  
 ![Esecuzione di un'istruzione nel codice](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Arrestare il debug e riavviarlo e, quando l'esecuzione si interrompe in corrispondenza del punto di interruzione, fare clic su **Debug/Esegui istruzione/** routine (oppure **Esegui istruzione** /routine sulla barra degli strumenti o **F10**). L'esecuzione si interrompe nuovamente in `Console.WriteLine("end");`.  
  
 Per ulteriori informazioni sull'esplorazione del codice con il debugger, vedere la pagina relativa all' [esplorazione del codice con il debugger](../debugger/navigating-through-code-with-the-debugger.md).
