---
title: Specificare dove copiare i file | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab842ce4f66684bf167d3cf627ce8cde82c5ea7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830375"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Procedura: Specificare il percorso in cui vengono copiati i file in Visual Studio
Quando si pubblica un'applicazione tramite ClickOnce, la proprietà `Publish Location` specifica il percorso in cui vengono inseriti i file dell'applicazione e il manifesto. Può trattarsi di un percorso di file o del percorso di un server FTP.  
  
 È possibile specificare la proprietà `Publish Location` nella pagina **Pubblica** di **Progettazione progetti** oppure mediante la Pubblicazione guidata. Per altre informazioni, vedere [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.  
  
### <a name="to-specify-a-publishing-location"></a>Per specificare un percorso di pubblicazione  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Nel campo **Percorso pubblicazione** immettere il percorso di pubblicazione usando uno dei formati seguenti:  
  
   - Per pubblicare in una condivisione file o in un percorso su disco, immettere il percorso usando un percorso UNC (*\\\Server\NomeApplicazione*) o un percorso file (*C:\Deploy\NomeApplicazione*).  
  
   - Per pubblicare in un server FTP, immettere il percorso nel formato <em>ftp://ftp.microsoft.com/\<NomeApplicazione></em>.  
  
     Si noti che il testo deve essere presente nella casella **Posizione di pubblicazione** perché il pulsante Sfoglia (**...**) funzioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)