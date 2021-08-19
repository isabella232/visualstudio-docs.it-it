---
title: Specificare il percorso da cui gli utenti finali installano
description: Informazioni su come impostare la proprietà URL di installazione, in cui è ospitata un'ClickOnce pubblicata per l'installazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: dae59aa3fb9bde3d2ed43cf7d8c41da4079cf408
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160608"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Procedura: Specificare il percorso da cui gli utenti finali eseguiranno l'installazione

Quando si pubblica un'applicazione, il percorso in cui gli utenti scaricano e installano l'applicazione non è necessariamente il percorso in cui si pubblica [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] inizialmente l'applicazione. Ad esempio, in alcune organizzazioni uno sviluppatore potrebbe pubblicare un'applicazione in un server di gestione temporanea e quindi un amministratore potrebbe spostare l'applicazione in un server Web.

In questo caso, è possibile usare la proprietà per specificare il server Web in cui gli utenti `Installation URL` andranno a scaricare l'applicazione. Questa operazione è necessaria in modo che il manifesto dell'applicazione sappia dove cercare gli aggiornamenti.

La `Installation URL` proprietà può essere impostata nella pagina **Pubblica** di Progettazione **Project .**

> [!NOTE]
> La `Installation URL` proprietà può essere impostata anche usando la **PublishWizard.** Per altre informazioni, vedere [Procedura: Pubblicare un'ClickOnce usando la Pubblicazione guidata.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

### <a name="to-specify-an-installation-url"></a>Per specificare un URL di installazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Nel campo URL di installazione immettere il percorso di installazione usando un URL completo nel formato o un `https://www.contoso.com/ApplicationName` percorso UNC nel formato `\Server\ApplicationName` .

## <a name="see-also"></a>Vedi anche
- [Procedura: Specificare il percorso in cui vengono copiati i file in Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Pubblicazione ClickOnce applicazioni](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'ClickOnce usando la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)