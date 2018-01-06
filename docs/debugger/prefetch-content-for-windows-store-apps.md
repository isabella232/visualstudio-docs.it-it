---
title: Eseguire il debug utilizzando il contenuto di prelettura nelle App UWP | Documenti Microsoft
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
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: f98867a5420755ca2eb4e2fb5e75070759a1a91b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Debug di App UWP con contenuto di prelettura in Visual Studio
![Si applica solo a Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Per rendere più la risposta dell'app UWP, è possibile richiedere Windows per precaricare parte del contenuto web, ad esempio immagini o pagine web, all'app [WinINet](http://msdn.microsoft.com/en-us/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)cache. Questa funzionalità, nota come "caricamento di contenuto in background", È particolarmente utile per il contenuto usato all'avvio, ma è possibile caricare in background altro contenuto usato di frequente, troppo. I metodi del [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) classe consentono di specificare l'URI del contenuto che si desidera precaricare. Vedi il Windows SDK [esempio prelettura di contenuto](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) per esempi relativi all'aggiunta della funzionalità ContentPrefetcher all'app.  
  
 Windows usa le regole euristiche per determinare quando e se caricare contenuto in background e quali risorse verranno scaricate. Le regole euristiche tengono conto delle condizioni di alimentazione e rete del sistema, della cronologia di utilizzo delle app utente e dei risultati dei precedenti tentativi di caricamento in background. In Visual Studio, è possibile utilizzare il **Trigger prelettura App di Windows Store** comando per forzare Windows a ignorare le regole euristiche ContentPrefetcher e a precaricare tutto il contenuto web specificato. Questo può essere utile se desideri testare le prestazioni o il comportamento dell'app con il contenuto da caricare in background in uno stato noto (caricato o meno).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Per forzare il precaricamento delle risorse specificate di ContentPrefetcher  
 Questa procedura presuppone che tu abbia già impostato la funzionalità ContentPrefetcher e specificato gli URI di contenuto da precaricare nel progetto dell'app. Per forzare il precaricamento del contenuto quando le risorse specificate sono nuove o modificate, devi avviare e arrestare l'app prima che venga scelto il **Trigger prelettura App di Windows Store** comando. Prima di tutto esegui l'app per registrare gli URI. **Trigger prelettura App di Windows Store** comando forza la funzionalità ContentPrefetcher a scaricare il contenuto e aggiungerlo nella cache. Nelle esecuzioni successive dell'app, puoi presupporre che il contenuto sia stato precaricato.  
  
1.  Avvia l'app per registrare gli URI del contenuto caricati in background con l'app. Nel **Debug** menu, scegliere **Avvia debug** (tasto di scelta rapida: F5).  
  
2.  Nel **Debug** menu, scegliere **Termina debug** (tasto di scelta rapida: MAIUSC + F5).  
  
3.  Nel **Debug** menu, scegliere **altre destinazioni Debug** e quindi scegliere **Trigger prelettura App di Windows Store**.  
  
 Ora puoi eseguire testare, analizzare o eseguire il debug dell'app con le risorse Web caricate in background.  
  
> [!NOTE]
>  Ripeti questi passaggi quando aggiungi o modifichi il contenuto Web specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Post di blog: trigger prelettura per applicazioni Windows Store in Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)