---
title: Specificare la modalità di installazione offline o online (ClickOnce)
description: Informazioni su come specificare la modalità di installazione per un'ClickOnce, che determina se l'applicazione è disponibile offline o online.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 68d51ae558c6bc40c632c680a76248b7ac1b4cb1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080520"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Procedura: Specificare la modalità di installazione online o offline di ClickOnce
`Install Mode`L'oggetto per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione determina se l'applicazione sarà disponibile offline o online. Quando si sceglie **L'applicazione** è disponibile solo online, l'utente deve avere accesso al percorso di pubblicazione (una pagina Web o una condivisione file) per poter [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eseguire l'applicazione. Quando si sceglie **Anche l'applicazione** è disponibile offline, l'applicazione aggiunge voci al menu **Start** e **alla** finestra di dialogo Installazione applicazioni . l'utente può eseguire l'applicazione quando non è connesso.

`Install Mode`L'oggetto può essere impostato nella pagina **Pubblica** di Progettazione **Project .**

> [!NOTE]
> `Install Mode`L'oggetto può essere impostato anche tramite la Pubblicazione guidata. Per altre informazioni, vedere [Procedura: Pubblicare un'applicazione ClickOnce tramite la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-make-a-clickonce-application-available-online-only"></a>Per rendere un'ClickOnce disponibile solo online

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. **Nell'area Modalità di installazione e Impostazioni** fare clic sul pulsante di opzione **L'applicazione è disponibile solo online.**

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Per rendere un'ClickOnce disponibile online o offline

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. **Nell'area Modalità di installazione e Impostazioni** fare clic sul pulsante di opzione **L'applicazione è disponibile anche offline.**

     Dopo l'installazione, l'applicazione aggiunge voci al menu **Start** e **a** Installazione applicazioni in Pannello di controllo.

## <a name="see-also"></a>Vedi anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'applicazione ClickOnce tramite la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)