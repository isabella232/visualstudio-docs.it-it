---
title: Specificare la modalità di installazione online o offline (ClickOnce)
description: Informazioni su come specificare la modalità di installazione per un'applicazione ClickOnce, che determina se l'applicazione è disponibile in modalità offline o online.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5236d73bb965d4f25634ad9e61a52608c9030146
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350933"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Procedura: Specificare la modalità di installazione online o offline di ClickOnce
`Install Mode`Per un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione determina se l'applicazione sarà disponibile in modalità offline o online. Quando si sceglie **l'applicazione è disponibile solo online** , l'utente deve avere accesso al percorso di pubblicazione, ovvero [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] una pagina Web o una condivisione file, per eseguire l'applicazione. Quando si sceglie **l'applicazione è disponibile anche offline** , l'applicazione aggiunge voci al menu **Start** e alla finestra di dialogo **Installazione applicazioni** ; l'utente è in grado di eseguire l'applicazione quando non è connessa.

Il `Install Mode` può essere impostato nella pagina **pubblica** di **Progettazione progetti**.

> [!NOTE]
> Il `Install Mode` può essere impostato anche tramite la pubblicazione guidata. Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-make-a-clickonce-application-available-online-only"></a>Per rendere un'applicazione ClickOnce disponibile solo online

1. Con un progetto selezionato in **Esplora soluzioni** , scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Nell'area **modalità di installazione e impostazioni** , fare clic sul pulsante di opzione **applicazione disponibile solo online** .

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Per rendere disponibile un'applicazione ClickOnce online o offline

1. Con un progetto selezionato in **Esplora soluzioni** , scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Nell'area **modalità di installazione e impostazioni** , fare clic sul pulsante di opzione **applicazione disponibile anche offline** .

     Quando è installato, l'applicazione aggiunge voci al menu **Start** e a installazione **applicazioni** nel pannello di controllo.

## <a name="see-also"></a>Vedere anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)