---
title: "Procedura: specificare il nome dal Menu Start per un'applicazione ClickOnce | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
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
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 98554ef2dc9b1f5bdd3ef1879f32b2c2319a7a1b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277778"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Procedura: specificare il nome di un'applicazione ClickOnce per il menu Start
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione è installata per l'uso sia online che offline, viene aggiunta una voce per il **avviare** dal menu e il **Aggiungi / Rimuovi programmi** elenco. Per impostazione predefinita, il nome visualizzato è identico al nome dell'assembly dell'applicazione, ma è possibile modificare il nome visualizzato, impostando **Product name** nel **Publish Options** nella finestra di dialogo.  
  
 **Nome del prodotto** verranno visualizzati nella pagina Publish. htm; per un'applicazione installata offline, sarà il nome della voce nel **avviare** menu che sarà anche il nome che mostra in **aggiungere o rimuovere Programmi**.  
  
 **Nome dell'editore** verranno visualizzati nella pagina Publish. htm **nome prodotto**, e per un'applicazione installata offline, lo sarà anche il nome della cartella che contiene l'icona dell'applicazione nel **Start**  menu.  
  
 È possibile impostare il **Product name** e **nome server di pubblicazione** le proprietà nel **Publish Options** della finestra di dialogo disponibile nel **pubblica** pagina del **Progettazione progetti**.  
  
### <a name="to-specify-a-start-menu-name"></a>Per specificare un nome di menu Start  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Scegliere il **pubblica** scheda.  
  
3.  Fare clic sui **le opzioni** pulsante per aprire il **Publish Options** nella finestra di dialogo.  
  
4.  Fare clic su **descrizione**.  
  
5.  Nel **Publish Options** finestra di dialogo immettere il nome da visualizzare nella **Product name**.  
  
6.  Facoltativamente, è possibile immettere un nome di server di pubblicazione nel **nome dell'editore**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



