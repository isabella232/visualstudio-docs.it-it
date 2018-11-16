---
title: 'Procedura: visualizzare le informazioni di traccia WPF | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a91d9f1f58a6905d50e14351bbbaf6fe732c60f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771252"
---
# <a name="how-to-display-wpf-trace-information"></a>Procedura: visualizzare le informazioni di traccia WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] può ricevere le informazioni di traccia di debug da applicazioni WPF e visualizzare tali informazioni nel **Output** finestra. Per visualizzare le informazioni di traccia di debug, è necessario abilitare la tracciatura WPF.  
  
 È possibile abilitare la tracciatura WPF nel file App.Config o a livello di codice utilizzando la classe <xref:System.Diagnostics.PresentationTraceSources>. Abilitare la tracciatura WPF in modo più semplice consiste nell'usare la **opzioni** finestra. La tracciatura WPF per applicazioni Web non è supportata.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Per abilitare o personalizzare le informazioni di traccia WPF  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nel **le opzioni** aperta la finestra di dialogo, nella casella a sinistra, il **debug** nodo.  
  
3.  Sotto **Debugging**, fare clic su **finestra Output**.  
  
4.  Sotto **impostazioni generali di Output**, selezionare **tutto l'output di debug**.  
  
5.  Nella casella a destra, cercare **impostazioni di traccia WPF**.  
  
6.  Aprire il **impostazioni di traccia WPF** nodo.  
  
7.  Sotto **impostazioni di traccia WPF**, fare clic sulla categoria di impostazioni che si desidera abilitare (ad esempio **Data Binding**).  
  
     Un controllo elenco a discesa viene visualizzato nella colonna Impostazioni accanto a **Data Binding** o qualsiasi categoria selezionata.  
  
8.  Fare clic sull'elenco a discesa e selezionare il tipo di informazioni di traccia che si desidera vedere: **tutte**, **critico**, **errore**, **avviso**,  **Le informazioni**, **Verbose**, o **ActivityTracing**.  
  
     **Critico** abilita la tracciatura di solo gli eventi critici.  
  
     **Errore** abilita la tracciatura di eventi critico ed errore.  
  
     **Avviso** abilita la tracciatura di critico, errore e gli eventi di avviso.  
  
     **Informazioni** abilita la tracciatura di eventi critico, errore, avviso e informazioni.  
  
     **Verbose** abilita la tracciatura di eventi critico, errore, avviso, informazioni e dettagliato.  
  
     **ActivityTracing** abilita la tracciatura di eventi di arresto, avvio, Suspend, trasferimento e ripresa.  
  
     Per ulteriori informazioni sul significato di questi livelli di informazioni di traccia, vedere <xref:System.Diagnostics.SourceLevels>.  
  
9. Fare clic su **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Per disabilitare le informazioni di traccia WPF  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nel **le opzioni** aperta la finestra di dialogo, nella casella a sinistra, il **debug** nodo.  
  
3.  Sotto **Debugging**, fare clic su **finestra Output**.  
  
4.  Nella casella a destra, cercare **impostazioni di traccia WPF**.  
  
5.  Aprire il **impostazioni di traccia WPF** nodo.  
  
6.  Sotto **impostazioni di traccia WPF**, fare clic sulla categoria di impostazioni che si desidera abilitare (ad esempio **Data Binding**).  
  
     Un controllo elenco a discesa viene visualizzato nella colonna Impostazioni accanto a **Data Binding** o qualsiasi categoria selezionata.  
  
7.  Fare clic sull'elenco a discesa e selezionare **disattivata**.  
  
8.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di WPF](../debugger/debugging-wpf.md)



