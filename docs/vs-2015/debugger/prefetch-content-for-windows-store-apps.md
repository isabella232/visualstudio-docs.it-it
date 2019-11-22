---
title: Prelettura del contenuto per le app di Windows Store | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ac6479b4dbb0815374174140deb0d660636ac9e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300520"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Prelettura del contenuto per le applicazioni Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica solo a Windows] (.. /Image windows_only_content. png "windows_only_content")  
  
 Per aumentare la velocità di risposta dell'app di Windows Store, è possibile richiedere a Windows di precaricare parte del contenuto Web, ad esempio immagini o pagine Web, nella cache [WinInet](https://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinInet](https://msdn.microsoft.com/library/aa383630.aspx)dell'app. Questa funzionalità, nota come "caricamento di contenuto in background", è particolarmente utile per il contenuto usato all'avvio, anche se puoi caricare in background altro contenuto usato di frequente. I metodi della classe [Windows.Networking.BackgroundTransfer.ContentPrefetcher](https://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) consentono di specificare gli URI del contenuto che desideri caricare in background.  
  
 Windows usa le regole euristiche per determinare quando e se caricare contenuto in background e quali risorse verranno scaricate. Le regole euristiche tengono conto delle condizioni di alimentazione e rete del sistema, della cronologia d'uso delle app utente e dei risultati dei precedenti tentativi di caricamento in background. In Visual Studio è possibile usare il comando **Trigger prelettura applicazioni Windows Store** per forzare Windows a ignorare le regole euristiche ContentPrefetcher e a precaricare tutto il contenuto Web specificato. Questo può essere utile se desideri testare le prestazioni o il comportamento dell'app con il contenuto da caricare in background in uno stato noto (caricato o meno).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Per forzare il precaricamento delle risorse specificate di ContentPrefetcher  
 Questa procedura presuppone che tu abbia già impostato la funzionalità ContentPrefetcher e specificato gli URI di contenuto da precaricare nel progetto dell'app. Per forzare il precaricamento del contenuto quando le risorse specificate sono nuove o modificate, avviare e arrestare l'app prima di scegliere il comando **Trigger prelettura applicazioni Windows Store**. Prima di tutto esegui l'app per registrare gli URI. Il comando **Trigger prelettura applicazioni Windows Store** forza la funzionalità ContentPrefetcher a scaricare il contenuto e ad aggiungerlo nella cache. Nelle esecuzioni successive dell'app, puoi presupporre che il contenuto sia stato precaricato.  
  
1. Avvia l'app per registrare gli URI del contenuto caricati in background con l'app. Scegliere **Avvia debug** (Tasto di scelta rapida: F5) dal menu **Debug**.  
  
2. Scegliere **Termina debug** dal menu **Debug** (Tasto di scelta rapida: MAIUSC+F5).  
  
3. Scegli **Altre destinazioni debug** dal menu **Debug**, quindi scegli **Trigger prelettura applicazioni Windows Store**.  
  
   Ora puoi eseguire testare, analizzare o eseguire il debug dell'app con le risorse Web caricate in background.  
  
> [!NOTE]
> Ripeti questi passaggi quando aggiungi o modifichi il contenuto Web specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Post di Blog: attivazione della prelettura per le app di Windows Store in Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)
