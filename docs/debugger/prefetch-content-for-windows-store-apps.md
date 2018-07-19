---
title: Eseguire il debug con contenuto preletto nelle App UWP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 458b320b971cbb3c4db74d6f2202455332ca5465
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056325"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Eseguire il debug delle App UWP con contenuto preletto in Visual Studio
  
 Per rendere più reattive le app UWP, è possibile richiedere Windows per precaricare parte del contenuto web, ad esempio immagini o pagine web, all'app [WinINet](/windows/desktop/WinInet/about-wininet) della cache. Questa funzionalità, nota come "caricamento di contenuto in background", È particolarmente utile per il contenuto usato all'avvio, ma è possibile eseguire la prelettura altri contenuti utilizzati frequentemente, troppo. I metodi del [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) classe consentono di specificare gli URI del contenuto che si vuole precaricare. Vedere il SDK di Windows [prelettura di contenuto esempio](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) per esempi su come aggiungere funzionalità ContentPrefetcher all'app.  
  
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