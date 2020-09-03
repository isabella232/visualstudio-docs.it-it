---
title: "Procedura: specificare una pagina di pubblicazione per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63356c6eb423ddead54290cc11c865a5102f55f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202167"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Procedura: specificare una pagina di pubblicazione per un'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si pubblica un' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione, viene generata e pubblicata una pagina Web predefinita (publish.htm) insieme all'applicazione. Questa pagina contiene il nome dell'applicazione, un collegamento per installare l'applicazione e/o tutti i prerequisiti e un collegamento a un argomento della guida che descrive [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . La proprietà **pubblica pagina** per il progetto consente di specificare un nome per la pagina Web per l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione.  
  
 Una volta specificata la pagina di pubblicazione, la prossima pubblicazione verrà copiata nel percorso di pubblicazione. non verrà sovrascritto se si esegue di nuovo la pubblicazione. Se si vuole personalizzare l'aspetto della pagina, è possibile farlo senza preoccuparsi di perdere le modifiche. Per altre informazioni, vedere [procedura: personalizzare la pagina Web predefinita di ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 È possibile impostare la proprietà **pagina** di pubblicazione nella finestra di dialogo **Opzioni di pubblicazione** accessibile dal riquadro **pubblica** di **Progettazione progetti**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Per specificare una pagina Web personalizzata per un'applicazione ClickOnce  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **proprietà**dal menu **progetto** .  
  
2. Selezionare il riquadro **pubblica** .  
  
3. Fare clic sul pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione** .  
  
4. Fare clic su **Distribuzione**.  
  
5. Nella finestra di dialogo **Opzioni di pubblicazione** assicurarsi che la casella di controllo **Apri la pagina Web di distribuzione dopo la pubblicazione** sia selezionata (per impostazione predefinita deve essere selezionata).  
  
6. Nella casella **pagina Web di distribuzione:** immettere il nome della pagina Web, quindi fare clic su **OK**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Per impedire l'avvio della pagina di pubblicazione ogni volta che si pubblica  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **proprietà**dal menu **progetto** .  
  
2. Selezionare il riquadro **pubblica** .  
  
3. Fare clic sul pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione** .  
  
4. Fare clic su **Distribuzione**.  
  
5. Nella finestra di dialogo **Opzioni di pubblicazione** deselezionare la casella di controllo **Apri la pagina Web di distribuzione dopo la pubblicazione** .  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Procedura: personalizzare la pagina Web predefinita ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)
