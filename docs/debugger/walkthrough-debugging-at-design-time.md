---
title: Eseguire il debug in fase di progettazione - Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1235e6360ccc5f6c0677f7ec9acb1dd85cad226
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180178"
---
# <a name="debug-at-design-time-in-visual-studio"></a>Eseguire il debug in fase di progettazione in Visual Studio

In alcuni scenari, è possibile eseguire il debug di codice in fase di progettazione anziché di tempo mentre l'applicazione è in esecuzione. È possibile farlo usando il **Immediate** finestra. Se si desidera eseguire il debug di codice XAML che interagisce con altro codice, ad esempio il codice di associazione dati, è possibile usare **Debug** > **Connetti a processo** a tale scopo.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Eseguire il debug in fase di progettazione utilizzando la finestra controllo immediata  

È possibile usare Visual Studio **Immediate** finestra per eseguire una funzione o subroutine mentre l'applicazione non è in esecuzione. Se la funzione o subroutine contiene un punto di interruzione, Visual Studio si interromperà l'esecuzione nel punto appropriato. È quindi possibile usare le finestre del debugger per esaminare lo stato del programma. Questa funzionalità è denominata debug in fase di progettazione.  

L'esempio seguente è in Visual Basic, ma il **Immediate** finestra è supportata anche nelle applicazioni c# e C++.
  
1.  Incollare il codice seguente in un'applicazione console Visual Basic:  
  
    ```vb  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Impostare un punto di interruzione sulla riga che legge, `s="Add BreakPoint Here"`.  
  
3.  Aprire il **controllo immediato** finestra (**Debug** > **Windows** > **immediato**) e digitare il comando seguente nel finestra: `?MyFunction<enter>`  
  
4.  Verificare che è stato raggiunto il punto di interruzione e che lo stack di chiamate è accurato.  
  
5.  Nel **Debug** menu, fare clic su **continua**e verificare che sia ancora in modalità progettazione.  
  
6.  Digitare il comando seguente nel **Immediate** finestra: `?MyFunction<enter>`  
  
7.  Digitare il comando seguente nel **Immediate** finestra: `?MySub<enter>`  
  
8.  Verificare che sia stato raggiunto il punto di interruzione ed esamina il valore della variabile statica `i` nella **variabili locali** finestra. Deve avere il valore di 3.  
  
9. Verificare che lo stack di chiamate è accurato.  
  
10. Nel **Debug** menu, fare clic su **continua**e verificare che sia ancora in modalità progettazione.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Eseguire il debug in fase di progettazione dalla finestra di progettazione XAML

Può essere utile eseguire il debug di code-behind dalla finestra di progettazione XAML in alcuni scenari di associazione dichiarativa dei dati.

1. Nel progetto, aggiungere una nuova pagina XAML, ad esempio *temp.xaml*. Lasciare vuota la nuova pagina XAML. 

1. Compilare la soluzione.

1. Aprire *temp.xaml*, che carica la finestra di progettazione (*UwpSurface.exe* in un'app UWP, o *XDesProc.exe*) in modo che è possibile collegarvi nei passaggi successivi. 

1. Aprire una nuova istanza di Visual Studio. Nella nuova istanza, aprire il **Connetti a processo** finestra di dialogo (**Debug** > **Connetti a processo**), impostare la **collegare a** campo al tipo di codice corretto, ad esempio **Managed Code (CoreCLR)** o il tipo di codice corretto in base la versione di .NET. Selezionare il processo di progettazione corretto dall'elenco e scegliere **Attach**.

    Per la piattaforma UWP progetti destinati a build 16299 o versione successiva, il processo di progettazione *UwpSurface.exe*. Per WPF o della piattaforma UWP in versioni precedenti a 16299, è il processo di progettazione *XDesProc.exe*.

1. Durante la connessione al processo, passare al progetto, aprire il code-behind in cui si desidera eseguire il debug e impostare un punto di interruzione.

1. Infine, aprire la pagina che contiene il codice XAML che include l'associazione dati.

    Ad esempio, è possibile impostare un punto di interruzione nel codice del convertitore di tipo per il seguente XAML, che associa un elemento TextBlock in fase di progettazione.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Quando la pagina viene caricata, viene raggiunto il punto di interruzione.
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debugger Basics](../debugger/getting-started-with-the-debugger.md) (Nozioni di base sul debugger)
