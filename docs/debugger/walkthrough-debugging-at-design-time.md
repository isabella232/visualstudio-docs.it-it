---
title: Eseguire il debug in fase di progettazione | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
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
ms.openlocfilehash: d9c4b0996faf26279ff8018e0e072fd25a33d783
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063422"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Eseguire il debug in fase di progettazione in Visual Studio (C#, C++, Visual Basic, F#)

Eseguire il debug di codice in fase di progettazione anziché durante un'app è in esecuzione, è possibile usare la **Immediate** finestra. 

Per eseguire il debug di codice XAML sottostante un'app dalla finestra di progettazione XAML, ad esempio il codice di associazione dati, è possibile usare **Debug** > **Connetti a processo**.
  
## <a name="use-the-immediate-window"></a>Utilizzare la finestra controllo immediata  

È possibile usare Visual Studio **Immediate** finestra per eseguire una funzione o subroutine senza eseguire l'app. Se la funzione o subroutine contiene un punto di interruzione, Visual Studio si interromperà nel punto di interruzione. È quindi possibile usare le finestre del debugger per esaminare lo stato del programma. Questa funzionalità è detta *debug in fase di progettazione*.  

Nell'esempio seguente è in Visual Basic. È anche possibile usare la **controllo immediato** in fase di progettazione nella finestra C#, F#e le app C++.

1. Incollare il codice seguente in un'app console di Visual Basic vuota:  
   
   ```vb  
   Module Module1
   
       Sub Main()
           MySub()
       End Sub
   
       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function
   
       Sub MySub()
           MyFunction()
   
       End Sub
   End Module
   ```  
   
1. Impostare un punto di interruzione sulla riga **funzione End**.  
   
1. Aprire il **controllo immediato** finestra selezionando **Debug** > **Windows** > **immediato**. Tipo di `?MyFunction` nella finestra e quindi premere **invio**.   
   
   Il punto di interruzione viene raggiunto e il valore della **MyFunction** nel **variabili locali** finestra è **1**. È possibile esaminare lo stack di chiamate e altre finestre di debug mentre l'app è in modalità di interruzione. 
   
1. Selezionare **continuazione** sulla barra degli strumenti di Visual Studio. L'app termina, e **1** viene restituito nel **immediato** finestra. Assicurarsi che si è ancora in modalità progettazione.  
   
1. Tipo di `?MyFunction` nella **controllo immediato** finestra nuovamente, quindi premere **invio**. Il punto di interruzione viene raggiunto e il valore della **MyFunction** nel **variabili locali** finestra è **2**. 
   
1. Senza selezionare **continuazione**, digitare `?MySub()` nel **immediato** finestra e quindi premere **invio**. Il punto di interruzione viene raggiunto e il valore della **MyFunction** nel **variabili locali** finestra è **3**. È possibile esaminare lo stato dell'app mentre l'app è in modalità di interruzione. 
   
1. Selezionare **continuare**. Il punto di interruzione viene nuovamente hit testing e il valore di **MyFunction** nel **variabili locali** finestra è ora **2**. Il **controllo immediato** finestra restituisce **espressione è stata valutata e non ha alcun valore**.
   
1. Selezionare **continuazione** nuovamente. L'app termina, e **2** viene restituito nel **immediato** finestra. Assicurarsi che sono ancora in modalità progettazione.
   
1. Per cancellare il contenuto del **controllo immediato** finestra, pulsante destro del mouse nella finestra e selezionare **Clear All**. 

## <a name="attach-to-an-app-from-the-xaml-designer"></a>Collega a un'app dalla finestra di progettazione XAML

In alcuni scenari di associazione dichiarativa dei dati, consente di eseguire il debug di code-behind nella finestra di progettazione XAML.

1. Nel progetto di Visual Studio, aggiungere una nuova pagina XAML, ad esempio *temp.xaml*. Lasciare vuota la nuova pagina XAML. 
   
1. Compilare la soluzione.
   
1. Aprire *temp.xaml*, che carica la finestra di progettazione, XAML *XDesProc.exe*, o *UwpSurface.exe* in un'app UWP. 
   
1. Aprire una nuova istanza di Visual Studio. Nella nuova istanza, selezionare **Debug** > **Connetti a processo**. 
   
1. Nel **Connetti a processo** finestra di dialogo, seleziona la finestra di progettazione processo dalle **processi disponibili** elenco.
   
   Per la piattaforma UWP progetti destinati a Windows build 16299 o versione successiva, il processo di progettazione *UwpSurface.exe*. Per WPF o UWP le versioni precedenti a 16299, è il processo di progettazione *XDesProc.exe*.
   
1. Assicurarsi che il **collegare** campo è impostato per il tipo di codice corretto per la versione di .NET, ad esempio **Managed Code (CoreCLR)**. 
   
1. Selezionare **collegare**.
   
1. Durante la connessione al processo, passare a altra istanza di Visual Studio e impostare i punti di interruzione in cui si desidera eseguire il debug di code-behind l'app.
   
   Ad esempio, è possibile impostare un punto di interruzione nel codice del convertitore di tipo per il seguente XAML, che associa un elemento TextBlock in fase di progettazione.
   
    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Quando la pagina viene caricata, viene raggiunto il punto di interruzione.
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Nozioni di base sul debugger](../debugger/getting-started-with-the-debugger.md)
