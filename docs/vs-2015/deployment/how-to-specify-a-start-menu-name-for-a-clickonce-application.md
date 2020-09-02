---
title: "Procedura: specificare il nome di un menu Start per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 30bb4050399bf7a6d9120f7e5454b26ce505af35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149767"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Procedura: specificare il nome di un'applicazione ClickOnce per il menu Start
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando un' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione viene installata per l'utilizzo online e offline, viene aggiunta una voce al menu **Start** e all'elenco **Installazione applicazioni** . Per impostazione predefinita, il nome visualizzato corrisponde al nome dell'assembly dell'applicazione, ma è possibile modificare il nome visualizzato impostando **nome prodotto** nella finestra di dialogo **Opzioni di pubblicazione** .  
  
 Il **nome del prodotto** verrà visualizzato nella pagina publish.htm; per un'applicazione offline installata, sarà il nome della voce nel menu **Start** , che sarà anche il nome che viene visualizzato in **installazione**applicazioni.  
  
 Il **nome del server di pubblicazione** verrà visualizzato nella pagina publish.htm sopra il nome del **prodotto**e, per un'applicazione offline installata, sarà anche il nome della cartella che contiene l'icona dell'applicazione nel menu **Start** .  
  
 È possibile impostare le proprietà **nome prodotto** e **nome server di pubblicazione** nella finestra di dialogo **Opzioni di pubblicazione** , disponibile nella pagina **pubblica** di **Progettazione progetti**.  
  
### <a name="to-specify-a-start-menu-name"></a>Per specificare il nome di un menu Start  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Fare clic sul pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione** .  
  
4. Fare clic su **Descrizione**.  
  
5. Nella finestra di dialogo **Opzioni di pubblicazione** immettere il nome da visualizzare in **Product Name**.  
  
6. Facoltativamente, è possibile immettere un nome del server di pubblicazione nel **nome dell'editore**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
