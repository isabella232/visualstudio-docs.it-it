---
title: Aggiornare un'applicazione (JavaScript) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e55e108901d9be62531e459f2b7805f86cfe6a08
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040641"
---
# <a name="refresh-an-app-javascript"></a>Aggiornare un'applicazione (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica a Windows e Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 È possibile apportare modifiche al codice mentre si sta eseguendo il debug e quindi aggiornarla un'app di Store utilizzando JavaScript scegliendo il **app di Windows di aggiornare** pulsante il **eseguire il Debug** sulla barra degli strumenti. Facendo clic su questo pulsante, l'app viene ricaricata senza arrestare e riavviare il debugger. La funzionalità di aggiornamento ti consente di modificare il codice HTML, CSS e JavaScript e visualizzare rapidamente i risultati. Questa funzionalità è supportata per app Windows Store e Windows Phone Store.  
  
 L'aggiornamento non mantiene lo stato dell'app né riflette le seguenti modifiche nell'app:  
  
- Modifiche al file manifesto del pacchetto, incluse le modifiche alle immagini specificato nel manifesto di pacchetto.  
  
- Modifiche dei riferimenti, ad esempio l'aggiunta o la rimozione di un riferimento SDK, o le modifiche ai componenti Windows Runtime (file con estensione winmd).  
  
- Modifiche delle risorse, ad esempio modifiche alle stringhe nei file con estensione resjson.  
  
- Modifiche dei file di progetto che causano modifiche dei nomi di percorso, nuovi file di progetto e file eliminati.  
  
- Modifiche delle proprietà di elementi e progetti, ad esempio modifiche al dispositivo di debug selezionato o modifiche all'azione del pacchetto per un file (nella finestra Proprietà).  
  
> [!IMPORTANT]
>  Quando modifichi i riferimenti, cambi il manifesto del pacchetto o apporti altre modifiche specificate nell'elenco precedente, devi arrestare e riavviare il debugger per aggiornare i file di origine HTML, CSS e JavaScript.  
  
### <a name="to-refresh-an-app"></a>Per aggiornare un'app  
  
1. In Visual Studio crea un nuovo progetto usando il modello di progetto Applicazione di navigazione.  
  
     Può trattarsi di un'app Windows Store, di un'app Windows Phone Store o di un'app universale.  
  
2. Con il modello aperto in Visual Studio, seleziona una destinazione di debug.  
  
     Se un progetto Windows Phone è il tuo attuale progetto di avvio, seleziona un'emulatore Windows Phone come destinazione di debug. In caso contrario, selezionare **simulatore** oppure **computer locale**.  
  
     ![Elenco di destinazioni di debug selezionare](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3. Premi F5 per eseguire l'app in modalità debug.  
  
4. Passa a Visual Studio. Premi F12.  
  
5. Nelle **Esplora soluzioni**, nella **pagine** > **home** cartella, Apri Home. HTML.  
  
6. Modificare il testo del titolo della pagina da  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     in un altro titolo, ad esempio:  
  
    ```html  
    Hello!  
    ```  
  
7. Fare clic sui **app di aggiornare Windows** pulsante, che ha un aspetto simile al seguente: ![Aggiorna il pulsante di app Windows](../debugger/media/js-refresh.png "JS_Refresh"). o premi F4.  
  
8. Torna all'app. L'app viene ricaricata senza riavviare il debugger e viene visualizzato il nuovo titolo della pagina.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio rapido: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)
