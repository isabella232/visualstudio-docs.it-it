---
title: Prelettura del contenuto per le app di Windows Store | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b01e0cd841c6239a7f2ef76f964482348ee16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526178"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Prelettura del contenuto per le applicazioni Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [prelettura del contenuto per le app di Windows Store](https://docs.microsoft.com/visualstudio/debugger/prefetch-content-for-windows-store-apps).  
  
Si applica solo a Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Per rendere più reattive all'app di Windows Store, è possibile richiedere Windows per precaricare parte del contenuto web, ad esempio immagini o pagine web, all'app [WinINet](http://msdn.microsoft.com/en-us/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)della cache. Questa funzionalità, nota come "caricamento di contenuto in background", è particolarmente utile per il contenuto usato all'avvio, anche se puoi caricare in background altro contenuto usato di frequente. I metodi del [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) classe consentono di specificare gli URI del contenuto che si vuole precaricare. Vedere il SDK di Windows [prelettura di contenuto esempio](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) per esempi su come aggiungere funzionalità ContentPrefetcher all'app.  
  
 Windows usa le regole euristiche per determinare quando e se caricare contenuto in background e quali risorse verranno scaricate. Le regole euristiche tengono conto delle condizioni di alimentazione e rete del sistema, della cronologia di utilizzo delle app utente e dei risultati dei precedenti tentativi di caricamento in background. In Visual Studio, è possibile usare la **Trigger prelettura applicazioni App di Windows Store** comando per forzare Windows a ignorare le regole euristiche ContentPrefetcher e a precaricare tutto il contenuto web specificato. Questo può essere utile se desideri testare le prestazioni o il comportamento dell'app con il contenuto da caricare in background in uno stato noto (caricato o meno).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Per forzare il precaricamento delle risorse specificate di ContentPrefetcher  
 Questa procedura presuppone che tu abbia già impostato la funzionalità ContentPrefetcher e specificato gli URI di contenuto da precaricare nel progetto dell'app. Per forzare il precaricamento del contenuto quando le risorse specificate sono nuove o modificate, devi avviare e arrestare l'app prima di scegliere la **Trigger prelettura applicazioni App di Windows Store** comando. Prima di tutto esegui l'app per registrare gli URI. **Trigger prelettura applicazioni Windows Store** comando forza la funzionalità ContentPrefetcher a scaricare il contenuto e aggiungerlo nella cache. Nelle esecuzioni successive dell'app, puoi presupporre che il contenuto sia stato precaricato.  
  
1.  Avvia l'app per registrare gli URI del contenuto caricati in background con l'app. Nel **Debug** menu, scegliere **Avvia debug** (tasto di scelta rapida: F5).  
  
2.  Nel **Debug** menu, scegliere **arresta debug** (tasto di scelta rapida: MAIUSC+F5).  
  
3.  Nel **Debug** menu, scegliere **altre destinazioni Debug** e quindi scegliere **Trigger prelettura applicazioni App di Windows Store**.  
  
 Ora puoi eseguire testare, analizzare o eseguire il debug dell'app con le risorse Web caricate in background.  
  
> [!NOTE]
>  Ripeti questi passaggi quando aggiungi o modifichi il contenuto Web specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Post di blog: trigger prelettura applicazioni per Windows Store Apps in Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)



