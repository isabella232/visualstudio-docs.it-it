---
title: Specificare una pagina di pubblicazione (ClickOnce app)
description: Informazioni su come impostare la proprietà Pubblica pagina per il progetto, che consente di specificare una pagina Web per l'ClickOnce applicazione.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: cfc043fc62bc99a8e292d89c9217dcb80e53f781
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146316"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce
Quando si pubblica un'applicazione, viene generata e pubblicata una pagina [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web predefinita (publish.htm) insieme all'applicazione. Questa pagina contiene il nome dell'applicazione, un collegamento per installare l'applicazione e/o eventuali prerequisiti e un collegamento a un argomento della Guida che descrive [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . La **proprietà Pubblica** pagina per il progetto consente di specificare un nome per la pagina Web per l'applicazione. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]

 Dopo aver specificato la pagina di pubblicazione, alla successiva pubblicazione verrà copiata nel percorso di pubblicazione. non verrà sovrascritto se si pubblica di nuovo. Se si vuole personalizzare l'aspetto della pagina, è possibile farlo senza preoccuparsi di perdere le modifiche. Per altre informazioni, vedere [Procedura: Personalizzare la ClickOnce Web predefinita.](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)

 La **proprietà Pubblica pagina** può essere impostata nella  finestra di dialogo **Opzioni** di pubblicazione , accessibile dal riquadro Pubblica di **Project Designer**.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Per specificare una pagina Web personalizzata per un'ClickOnce personalizzata

1. Con un progetto selezionato in **Esplora soluzioni**, nel menu **Project** fare clic su **Proprietà**.

2. Selezionare il **riquadro** Pubblica.

3. Fare clic **sul pulsante** Opzioni per aprire la finestra di **dialogo Opzioni** di pubblicazione .

4. Fare clic su **Distribuzione**.

5. Nella finestra **di dialogo Opzioni** di pubblicazione assicurarsi che la casella di controllo Apri pagina **Web** di distribuzione dopo la pubblicazione sia selezionata (deve essere selezionata per impostazione predefinita).

6. Nella casella **Pagina Web di distribuzione** immettere il nome della pagina Web e quindi fare clic su **OK.**

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Per impedire l'avvio della pagina di pubblicazione ogni volta che si pubblica

1. Con un progetto selezionato in **Esplora soluzioni**, nel menu **Project** fare clic su **Proprietà**.

2. Selezionare il **riquadro** Pubblica.

3. Fare clic **sul pulsante** Opzioni per aprire la finestra di **dialogo Opzioni** di pubblicazione .

4. Fare clic su **Distribuzione**.

5. Nella finestra **di dialogo Opzioni** di pubblicazione deselezionare la casella di controllo Apri pagina Web **di** distribuzione dopo la pubblicazione .

## <a name="see-also"></a>Vedi anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'ClickOnce usando la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Procedura: Personalizzare la pagina Web predefinita ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)