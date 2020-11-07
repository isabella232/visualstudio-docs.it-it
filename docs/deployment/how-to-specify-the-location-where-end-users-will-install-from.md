---
title: Specificare il percorso da cui gli utenti finali installano
description: Informazioni su come impostare la proprietà URL di installazione, in cui è ospitata un'applicazione ClickOnce pubblicata per l'installazione.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3518a2eef331414e5c73c0cebb36681ad2b72d61
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349620"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Procedura: Specificare il percorso da cui gli utenti finali eseguiranno l'installazione

Quando si pubblica un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, la posizione in cui gli utenti accedono per scaricare e installare l'applicazione non è necessariamente la posizione in cui viene inizialmente pubblicata l'applicazione. In alcune organizzazioni, ad esempio, uno sviluppatore potrebbe pubblicare un'applicazione in un server di staging e quindi un amministratore sposta l'applicazione in un server Web.

In questo caso, è possibile usare la `Installation URL` proprietà per specificare il server Web in cui gli utenti useranno per scaricare l'applicazione. Questa operazione è necessaria affinché il manifesto dell'applicazione sappia dove cercare gli aggiornamenti.

La `Installation URL` proprietà può essere impostata nella pagina **pubblica** di **Progettazione progetti**.

> [!NOTE]
> La `Installation URL` proprietà può essere impostata anche usando **pubblicazione guidata**. Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Per specificare un URL di installazione

1. Con un progetto selezionato in **Esplora soluzioni** , scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Nel campo URL di installazione immettere il percorso di installazione utilizzando un URL completo utilizzando il formato `https://www.contoso.com/ApplicationName` o un percorso UNC utilizzando il formato `\Server\ApplicationName` .

## <a name="see-also"></a>Vedere anche
- [Procedura: Specificare il percorso in cui vengono copiati i file in Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)