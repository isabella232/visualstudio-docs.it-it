---
title: 'Procedura: specificare il percorso da cui gli utenti finali installeranno | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 993c654ccd16f2d51d86a46a716edd611ae154dd
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557608"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Procedura: Specificare il percorso da cui gli utenti finali eseguiranno l'installazione
Quando si pubblica un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la posizione in cui gli utenti accedono per scaricare e installare l'applicazione non è necessariamente la posizione in cui viene inizialmente pubblicata l'applicazione. In alcune organizzazioni, ad esempio, uno sviluppatore potrebbe pubblicare un'applicazione in un server di staging e quindi un amministratore sposta l'applicazione in un server Web.

In questo caso, è possibile usare la proprietà `Installation URL` per specificare il server Web in cui gli utenti useranno per scaricare l'applicazione. Questa operazione è necessaria affinché il manifesto dell'applicazione sappia dove cercare gli aggiornamenti.

È possibile impostare la proprietà `Installation URL` nella pagina **pubblica** di **Progettazione progetti**.

> [!NOTE]
> È inoltre possibile impostare la proprietà `Installation URL` utilizzando **pubblicazione guidata**. Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Per specificare un URL di installazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Nel campo URL di installazione immettere il percorso di installazione utilizzando un URL completo utilizzando il formato `https://www.contoso.com/ApplicationName`o un percorso UNC utilizzando il formato `\Server\ApplicationName`.

## <a name="see-also"></a>Vedere anche
- [Procedura: Specificare il percorso in cui vengono copiati i file in Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)