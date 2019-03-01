---
title: "Procedura: specificare una pagina di pubblicazione per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12a7d9dd2ad9d329fda5f27e78e24b0aa07cc3a6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598921"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce
Quando si pubblica un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione, una pagina Web predefinita (Publish. htm) viene generata e pubblicata insieme all'applicazione. Questa pagina contiene il nome di un collegamento a un argomento della Guida che descrive l'applicazione e un collegamento per installare l'applicazione e/o gli eventuali prerequisiti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Il **pagina di pubblicazione** proprietà del progetto consente di specificare un nome per la pagina Web per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.

 Dopo la pagina di pubblicazione è stata specificata, la volta successiva che si pubblica, verrà copiato nel percorso di pubblicazione; non verrà sovrascritto se si pubblica nuovamente. Se si vuole personalizzare l'aspetto della pagina, è possibile farlo senza doversi preoccupare di perdere le modifiche apportate. Per altre informazioni, vedere [procedura: personalizzare la pagina Web predefinita ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).

 Il **pagina di pubblicazione** proprietà può essere impostata **Publish Options** finestra di dialogo, accessibile dal **Publish** riquadro del **Progettazione progetti**.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Per specificare una pagina Web personalizzata per un'applicazione ClickOnce

1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2.  Selezionare il **pubblica** riquadro.

3.  Fare clic sui **le opzioni** pulsante per aprire il **Publish Options** nella finestra di dialogo.

4.  Fare clic su **distribuzione**.

5.  Nel **Publish Options** finestra di dialogo, assicurarsi che le **distribuzione Apri pagina web dopo la pubblicazione** casella di controllo è selezionata (deve essere selezionato per impostazione predefinita).

6.  Nel **pagina web di distribuzione** casella, immettere il nome della pagina Web e quindi fare clic su **OK**.

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Per impedire l'avvio ogni volta che si pubblica la pagina di pubblicazione

1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2.  Selezionare il **pubblica** riquadro.

3.  Fare clic sui **le opzioni** pulsante per aprire il **Publish Options** nella finestra di dialogo.

4.  Fare clic su **distribuzione**.

5.  Nel **Publish Options** della finestra di dialogo deseleziona le **pagina web di distribuzione aperto dopo la pubblicazione** casella di controllo.

## <a name="see-also"></a>Vedere anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Procedura: Personalizzare la pagina Web predefinita ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)