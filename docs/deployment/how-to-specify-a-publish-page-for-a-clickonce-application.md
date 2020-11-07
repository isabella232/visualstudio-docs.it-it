---
title: Specificare una pagina di pubblicazione (app ClickOnce)
description: Informazioni su come impostare la proprietà pubblica pagina per il progetto, che consente di specificare una pagina Web per l'applicazione ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: ecf70f5ffdd81688943892c06fdf98aae73d6c57
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350959"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce
Quando si pubblica un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, viene generata e pubblicata una pagina Web predefinita (publish.htm) insieme all'applicazione. Questa pagina contiene il nome dell'applicazione, un collegamento per installare l'applicazione e/o tutti i prerequisiti e un collegamento a un argomento della guida che descrive [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . La proprietà **pubblica pagina** per il progetto consente di specificare un nome per la pagina Web per l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione.

 Una volta specificata la pagina di pubblicazione, la prossima pubblicazione verrà copiata nel percorso di pubblicazione. non verrà sovrascritto se si esegue di nuovo la pubblicazione. Se si vuole personalizzare l'aspetto della pagina, è possibile farlo senza preoccuparsi di perdere le modifiche. Per altre informazioni, vedere [procedura: personalizzare la pagina Web predefinita di ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).

 È possibile impostare la proprietà **pagina** di pubblicazione nella finestra di dialogo **Opzioni di pubblicazione** accessibile dal riquadro **pubblica** di **Progettazione progetti**.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Per specificare una pagina Web personalizzata per un'applicazione ClickOnce

1. Con un progetto selezionato in **Esplora soluzioni** , scegliere **proprietà** dal menu **progetto** .

2. Selezionare il riquadro **pubblica** .

3. Fare clic sul pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione** .

4. Fare clic su **Distribuzione**.

5. Nella finestra di dialogo **Opzioni di pubblicazione** assicurarsi che la casella di controllo **Apri la pagina Web di distribuzione dopo la pubblicazione** sia selezionata (per impostazione predefinita deve essere selezionata).

6. Nella casella **pagina Web di distribuzione** immettere il nome della pagina Web, quindi fare clic su **OK**.

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Per impedire l'avvio della pagina di pubblicazione ogni volta che si pubblica

1. Con un progetto selezionato in **Esplora soluzioni** , scegliere **proprietà** dal menu **progetto** .

2. Selezionare il riquadro **pubblica** .

3. Fare clic sul pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione** .

4. Fare clic su **Distribuzione**.

5. Nella finestra di dialogo **Opzioni di pubblicazione** deselezionare la casella di controllo **Apri la pagina Web di distribuzione dopo la pubblicazione** .

## <a name="see-also"></a>Vedere anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Procedura: Personalizzare la pagina Web predefinita ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)