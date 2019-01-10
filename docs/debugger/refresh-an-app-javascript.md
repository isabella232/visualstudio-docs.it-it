---
title: Aggiornare un'app UWP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 43f232157ef9237ba9d401f473ab0db1b1260f40
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828723"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Aggiornare un'app UWP in Visual Studio
  
 È possibile apportare modifiche al codice mentre si sta eseguendo il debug e quindi aggiornarla un'app UWP con JavaScript scegliendo il **app di Windows di aggiornare** pulsante il **eseguire il Debug** sulla barra degli strumenti. Facendo clic su questo pulsante, l'app viene ricaricata senza arrestare e riavviare il debugger. La funzionalità di aggiornamento ti consente di modificare il codice HTML, CSS e JavaScript e visualizzare rapidamente i risultati. Questa funzionalità è supportata per le app UWP.  
  
 L'aggiornamento non mantiene lo stato dell'app né riflette le seguenti modifiche nell'app:  
  
-   Modifiche al file manifesto del pacchetto, incluse le modifiche alle immagini specificato nel manifesto di pacchetto.  
  
-   Modifiche dei riferimenti, ad esempio l'aggiunta o la rimozione di un riferimento SDK, o le modifiche ai componenti Windows Runtime (file con estensione winmd).  
  
-   Modifiche delle risorse, ad esempio modifiche alle stringhe nei file con estensione resjson.  
  
-   Modifiche dei file di progetto che causano modifiche dei nomi di percorso, nuovi file di progetto e file eliminati.  
  
-   Modifiche delle proprietà di elementi e progetti, ad esempio modifiche al dispositivo di debug selezionato o modifiche all'azione del pacchetto per un file (nella finestra Proprietà).  
  
> [!IMPORTANT]
>  Quando modifichi i riferimenti, cambi il manifesto del pacchetto o apporti altre modifiche specificate nell'elenco precedente, devi arrestare e riavviare il debugger per aggiornare i file di origine HTML, CSS e JavaScript.  
  
### <a name="to-refresh-an-app"></a>Per aggiornare un'app  
  
1.  Con il progetto UWP aperto in Visual Studio, selezionare **computer locale** come destinazione di debug.
  
     ![Elenco di destinazioni di debug selezionare](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  Premi F5 per eseguire l'app in modalità debug.  
  
4.  Passa a Visual Studio. 
  
5.  Nella home page dell'app UWP, modificare parte del codice HTML.
  
7.  Fai clic sul pulsante Aggiorna applicazione Windows **, che ha un aspetto simile a**  ![Aggiorna il pulsante di app Windows](../debugger/media/js_refresh.png "JS_Refresh"). o premi F4.  
  
8.  Torna all'app. L'app viene ricaricata e il codice HTML aggiornato è utilizzato per il rendering dell'app.
  
## <a name="see-also"></a>Vedere anche  
 [Avvio rapido: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)