---
title: "Procedura: Specificare il nome dal Menu Start per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2ac32b9be940883953d69e0347ffa5e12d5407a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945619"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Procedura: Specificare il nome di un'applicazione ClickOnce per il menu Start
Quando un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione è installata per l'uso sia online che offline, viene aggiunta una voce per il **avviare** dal menu e il **Aggiungi / Rimuovi programmi** elenco. Per impostazione predefinita, il nome visualizzato è identico al nome dell'assembly dell'applicazione, ma è possibile modificare il nome visualizzato, impostando **Product name** nel **Publish Options** nella finestra di dialogo.  
  
 **Nome del prodotto** verrà visualizzato nel *Publish. htm* pagina, per un'applicazione installata offline, ma sarà il nome della voce nel **avviare** menu che sarà anche il nome che mostra in **Aggiungere o rimuovere programmi**.  
  
 **Nome dell'editore** verranno visualizzati nella *Publish. htm* pagina precedente **Product name**, e per un'applicazione installata offline, lo sarà anche il nome della cartella che contiene l'applicazione icona nel **avviare** menu.  

 Il riferimento di scelta rapida o un'app dal menu Start viene creato nel *%appdata%\Microsoft\Windows\Start %SystemDrive%\programdata\microsoft\windows\start Menu\Programmi.\\< nome del server di pubblicazione\>*. Il riferimento di scelta rapida o un'app ha lo stesso nome come nome di prodotto.
  
 È possibile impostare il **Product name** e **nome server di pubblicazione** le proprietà nel **Publish Options** della finestra di dialogo disponibile nel **pubblica** pagina del **Progettazione progetti**.  
  
### <a name="to-specify-a-start-menu-name"></a>Per specificare un nome di menu Start  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Pubblica**.  
  
3.  Fare clic sui **le opzioni** pulsante per aprire il **Publish Options** nella finestra di dialogo.  
  
4.  Fare clic su **descrizione**.  
  
5.  Nel **Publish Options** finestra di dialogo immettere il nome da visualizzare nella **Product name**.  
  
6.  Facoltativamente, è possibile immettere un nome di server di pubblicazione nel **nome dell'editore**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)