---
title: 'Procedura: specificare la modalità Offline o ClickOnce modalità di installazione Online | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 7f277966070e142ebc24d70acfcf4bf5502f419a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526994"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Procedura: specificare la modalità di installazione online o offline di ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: specificare la modalità Offline di ClickOnce o installare la modalità Online](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-the-clickonce-offline-or-online-install-mode).  
  
Il `Install Mode` per un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione determina se l'applicazione sarà disponibile online o offline. Quando si sceglie **l'applicazione è disponibile solo online**, l'utente deve avere accesso al [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] posizione (una pagina Web o una condivisione file) per eseguire l'applicazione di pubblicazione. Quando si sceglie **l'applicazione è disponibile offline nonché**, l'applicazione aggiunge voci per il **avviare** menu e le **Aggiungi / Rimuovi programmi** nella finestra di dialogo; l'utente è in grado di eseguire l'applicazione quando non sono connessi.  
  
 Il `Install Mode` può essere impostata sul **Publish** pagina del **creazione progetti**.  
  
 **Nota** il `Install Mode` può essere impostato anche usando la pubblicazione guidata. Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Per rendere un'applicazione ClickOnce disponibile solo online  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Scegliere il **pubblica** scheda.  
  
3.  Nel **installare la modalità e le impostazioni** area, fare clic sui **l'applicazione è disponibile solo online** pulsante di opzione.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Per rendere disponibile un'applicazione ClickOnce online o offline  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Scegliere il **pubblica** scheda.  
  
3.  Nel **installare la modalità e le impostazioni** area, fare clic sui **l'applicazione è disponibile offline nonché** pulsante di opzione.  
  
     Durante l'installazione, l'applicazione aggiunge voci per il **avviare** dal menu e di ottenere **Aggiungi / Rimuovi programmi** nel Pannello di controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



