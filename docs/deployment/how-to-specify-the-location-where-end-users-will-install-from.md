---
title: "Procedura: specificare il percorso in cui gli utenti finali eseguiranno l'installazione da | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b0731a5e218b6fcd6a13ac00fe19daad86f6b3d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078085"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Procedura: specificare il percorso in cui gli utenti finali eseguiranno l'installazione da
Quando si pubblica un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione, la posizione in cui gli utenti potranno scaricare e installare l'applicazione non è necessariamente la posizione in cui inizialmente l'applicazione viene pubblicata. Ad esempio, in alcune organizzazioni lo sviluppatore può pubblicare un'applicazione in un server di gestione temporanea e quindi un amministratore potrebbe spostare l'applicazione in un server Web.  
  
 In questo caso, è possibile usare il `Installation URL` proprietà per specificare il server Web cui accederanno gli utenti di scaricare l'applicazione. Ciò è necessario in modo che il manifesto dell'applicazione sappia dove cercare gli aggiornamenti.  
  
 Il `Installation URL` può impostare la proprietà il **Publish** pagina del **creazione progetti**.  
  
 **Nota** il `Installation URL` proprietà può essere impostata inoltre mediante il **pubblicazione guidata**. Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Per specificare un URL di installazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Scegliere il **pubblica** scheda.  
  
3.  Nel campo URL di installazione, immettere il percorso di installazione tramite un URL completo nel formato *http://www.microsoft.com/ApplicationName*, o un percorso UNC nel formato  *\\\Server\ApplicationName*.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: specificare in cui vengono copiati i file di Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)