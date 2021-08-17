---
title: Specificare dove copiare i file | Microsoft Docs
description: Informazioni su come impostare la proprietà Percorso di pubblicazione per un'ClickOnce, che specifica il percorso in cui vengono inseriti i file e il manifesto dell'applicazione.
ms.custom:
- SEO-VS-2020
- seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 2425f428f5252c574eacb17c1c404bf06f80279e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080442"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Procedura: Specificare il percorso in cui vengono copiati i file in Visual Studio
Quando si pubblica un'applicazione tramite ClickOnce, la proprietà `Publish Location` specifica il percorso in cui vengono inseriti i file dell'applicazione e il manifesto. Può trattarsi di un percorso di file o del percorso di un server FTP.

 È possibile specificare la proprietà `Publish Location` nella pagina **Pubblica** di **Progettazione progetti** oppure mediante la Pubblicazione guidata. Per altre informazioni, vedere [Procedura: Pubblicare un'ClickOnce usando la Pubblicazione guidata.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

> [!NOTE]
> Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.

### <a name="to-specify-a-publishing-location"></a>Per specificare un percorso di pubblicazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Nel campo **Percorso pubblicazione** immettere il percorso di pubblicazione usando uno dei formati seguenti:

   - Per pubblicare in una condivisione file o in un percorso su disco, immettere il percorso usando un percorso UNC (*\\ \Server\ApplicationName*) o un percorso di file (*C:\Deploy\ApplicationName*).

   - Per pubblicare in un server FTP, immettere il percorso usando il <em>formato ftp://ftp.microsoft.com/ \<ApplicationName> </em>.

     Si noti che il testo deve essere presente nella casella **Posizione** di pubblicazione per consentire il funzionamento del pulsante Sfoglia **(**... ).

## <a name="see-also"></a>Vedi anche
- [Pubblicazione ClickOnce applicazioni](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'ClickOnce di pubblicazione usando la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)