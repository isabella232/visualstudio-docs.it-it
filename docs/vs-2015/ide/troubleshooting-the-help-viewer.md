---
title: Risoluzione dei problemi del Visualizzatore della Guida | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 29c7ee223bbfbeb2dd7b262c33d6c00ea3c41411
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245544"
---
# <a name="troubleshooting-the-help-viewer"></a>Risoluzione dei problemi relativi al visualizzatore della Guida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento vengono illustrati i problemi che potrebbero verificarsi con il visualizzatore della Guida.  
  
## <a name="audio-doesnt-work"></a>L'audio non funziona.  
 Il visualizzatore della Guida non include un lettore audio. Se si scaricano contenuti che includono l'audio e non accade nulla quando si sceglie **Riproduci**, installare un lettore audio.  
  
## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>La ricerca non funziona in Windows Server 2008, Windows Server 2008 con SP1 o Windows Server 2008 R2.  
 Le funzionalità di ricerca e filtro nel visualizzatore della Guida richiedono il servizio Windows Search. Per impostazione predefinita, questo servizio è disattivato in Windows Server 2008, Windows Server 2008 con Service Pack 1 (SP1) e Windows Server 2008 R2.  
  
#### <a name="to-activate-windows-search-service"></a>Per attivare il servizio Windows Search  
  
1.  Avviare Server Manager.  
  
2.  Nel riquadro di spostamento a sinistra scegliere **Ruoli**.  
  
3.  Nel riquadro Riepilogo ruoli scegliere **Aggiungi ruolo**.  
  
4.  Scegliere il ruolo Servizi file e il pulsante **Avanti**.  
  
5.  Scegliere il servizio ruolo Windows Search.  
  
## <a name="additional-resources"></a>Risorse aggiuntive  
 È possibile ottenere altre informazioni e offrire commenti e suggerimenti sul visualizzatore della Guida mediante le risorse seguenti:  
  
-   Per offrire commenti e suggerimenti, vedere [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) dal sito Microsoft o inviare un messaggio di posta elettronica a [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
-   Per altre informazioni, vedere la [sistema di Guida e documentazione per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=232741) forum e [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743) blog.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di Help Viewer 2.1 amministratore](http://go.microsoft.com/fwlink/?LinkId=243985)



