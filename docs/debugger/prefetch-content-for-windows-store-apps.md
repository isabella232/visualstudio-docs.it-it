---
title: Eseguire il debug con contenuto preletto nelle App UWP | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 6f8ebe41f2775dddd5f70c654e21c7dc64adc44e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835197"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Eseguire il debug delle App UWP con contenuto preletto in Visual Studio
  
 Per rendere più reattive le app UWP, è possibile richiedere Windows per precaricare parte del contenuto web, ad esempio immagini o pagine web, all'app [WinINet](/windows/desktop/WinInet/about-wininet) della cache. Questa funzionalità, nota come "caricamento di contenuto in background", è particolarmente utile per il contenuto usato all'avvio, anche se puoi caricare in background altro contenuto usato di frequente. I metodi della classe [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) consentono di specificare gli URI del contenuto che desideri caricare in background. Per esempi relativi all'aggiunta della funzionalità ContentPrefetcher all'app, vedere Windows SDK [Content prefetch sample](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) (Esempio di caricamento in background di contenuto).  
  
 Windows usa le regole euristiche per determinare quando e se caricare contenuto in background e quali risorse verranno scaricate. Le regole euristiche tengono conto delle condizioni di alimentazione e rete del sistema, della cronologia di utilizzo delle app utente e dei risultati dei precedenti tentativi di caricamento in background. In Visual Studio è possibile usare il comando **Trigger prelettura applicazioni Windows Store** per forzare Windows a ignorare le regole euristiche ContentPrefetcher e a precaricare tutto il contenuto Web specificato. Questo può essere utile se desideri testare le prestazioni o il comportamento dell'app con il contenuto da caricare in background in uno stato noto (caricato o meno).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Per forzare il precaricamento delle risorse specificate di ContentPrefetcher  
 Questa procedura presuppone che tu abbia già impostato la funzionalità ContentPrefetcher e specificato gli URI di contenuto da precaricare nel progetto dell'app. Per forzare il precaricamento del contenuto quando le risorse specificate sono nuove o modificate, avviare e arrestare l'app prima di scegliere il comando **Trigger prelettura applicazioni Windows Store**. Prima di tutto esegui l'app per registrare gli URI. Il comando **Trigger prelettura applicazioni Windows Store** forza la funzionalità ContentPrefetcher a scaricare il contenuto e ad aggiungerlo nella cache. Nelle esecuzioni successive dell'app, puoi presupporre che il contenuto sia stato precaricato.  
  
1. Avvia l'app per registrare gli URI del contenuto caricati in background con l'app. Scegli **Avvia debug**  (Tasto di scelta rapida: F5) dal menu **Debug** .  
  
2. Nel **Debug** menu, scegliere **arresta debug** (tasto di scelta rapida: MAIUSC + F5).  
  
3. Scegli **Altre destinazioni debug** dal menu **Debug**, quindi scegli **Trigger prelettura applicazioni Windows Store**.  
  
   Ora puoi eseguire testare, analizzare o eseguire il debug dell'app con le risorse Web caricate in background.  
  
> [!NOTE]
>  Ripeti questi passaggi quando aggiungi o modifichi il contenuto Web specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Post di blog Trigger prelettura per le app di Windows Store in Visual Studio 2013 Update 2](https://blogs.msdn.microsoft.com/devops/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)