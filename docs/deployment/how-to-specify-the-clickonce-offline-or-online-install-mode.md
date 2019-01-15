---
title: 'Procedura: Specificare la modalità Offline o ClickOnce modalità di installazione Online | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd0b985d7629ec282de4946ab89fef06e97c5921
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889014"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Procedura: Specificare la modalità di installazione online o offline di ClickOnce
Il `Install Mode` per un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione determina se l'applicazione sarà disponibile online o offline. Quando si sceglie **l'applicazione è disponibile solo online**, l'utente deve avere accesso al [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] posizione (una pagina Web o una condivisione file) per eseguire l'applicazione di pubblicazione. Quando si sceglie **l'applicazione è disponibile offline nonché**, l'applicazione aggiunge voci per il **avviare** menu e le **Aggiungi / Rimuovi programmi** nella finestra di dialogo; l'utente è in grado di eseguire l'applicazione quando non sono connessi.  
  
 Il `Install Mode` può essere impostata sul **Publish** pagina del **creazione progetti**.  
  
 **Nota** il `Install Mode` può essere impostato anche usando la pubblicazione guidata. Per altre informazioni, vedere [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Per rendere un'applicazione ClickOnce disponibile solo online  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Pubblica**.  
  
3.  Nel **installare la modalità e le impostazioni** area, fare clic sui **l'applicazione è disponibile solo online** pulsante di opzione.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Per rendere disponibile un'applicazione ClickOnce online o offline  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Pubblica**.  
  
3.  Nel **installare la modalità e le impostazioni** area, fare clic sui **l'applicazione è disponibile offline nonché** pulsante di opzione.  
  
     Durante l'installazione, l'applicazione aggiunge voci per il **avviare** dal menu e di ottenere **Aggiungi / Rimuovi programmi** nel Pannello di controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)