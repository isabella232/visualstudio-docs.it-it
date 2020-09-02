---
title: 'Procedura: specificare la modalità di installazione online o offline di ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4111ca5aee4a405a4a797dbfee14a3d4b50435f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149744"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Procedura: specificare la modalità di installazione online o offline di ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Install Mode`Per un' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione determina se l'applicazione sarà disponibile in modalità offline o online. Quando si sceglie **l'applicazione è disponibile solo online**, l'utente deve avere accesso al percorso di pubblicazione, ovvero [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] una pagina Web o una condivisione file, per eseguire l'applicazione. Quando si sceglie **l'applicazione è disponibile anche offline**, l'applicazione aggiunge voci al menu **Start** e alla finestra di dialogo **Installazione applicazioni** ; l'utente è in grado di eseguire l'applicazione quando non è connessa.  
  
 Il `Install Mode` può essere impostato nella pagina **pubblica** di **Progettazione progetti**.  
  
 **Nota** Il `Install Mode` può essere impostato anche tramite la pubblicazione guidata. Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Per rendere un'applicazione ClickOnce disponibile solo online  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Nell'area **modalità di installazione e impostazioni** , fare clic sul pulsante di opzione **applicazione disponibile solo online** .  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Per rendere disponibile un'applicazione ClickOnce online o offline  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Nell'area **modalità di installazione e impostazioni** , fare clic sul pulsante di opzione **applicazione disponibile anche offline** .  
  
     Quando è installato, l'applicazione aggiunge voci al menu **Start** e a installazione **applicazioni** nel pannello di controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
