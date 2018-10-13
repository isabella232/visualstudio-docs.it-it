---
title: 'Procedura: specificare in cui vengono copiati i file di Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 76967e02d730b06438136bb0354ce5a67a648ea4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188656"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Procedura: specificare il percorso in cui vengono copiati i file in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si pubblica un'applicazione tramite ClickOnce, la proprietà `Publish Location` specifica il percorso in cui vengono inseriti i file dell'applicazione e il manifesto. Può trattarsi di un percorso di file o del percorso di un server FTP.  
  
 È possibile specificare il `Publish Location` proprietà il **Publish** pagina del **creazione progetti**, oppure usando la pubblicazione guidata. Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.  
  
### <a name="to-specify-a-publishing-location"></a>Per specificare un percorso di pubblicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Scegliere il **pubblica** scheda.  
  
3.  Nel **percorso di pubblicazione** immettere il percorso di pubblicazione usando uno dei formati seguenti:  
  
    -   Per pubblicare in un percorso di condivisione o un disco del file, immettere il percorso utilizzando un percorso UNC (\\\Server\ApplicationName) o un percorso di file (C:\Deploy\ApplicationName).  
  
    -   Per pubblicare in un server FTP, immettere il percorso nel formato ftp://ftp.microsoft.com/NomeApplicazione.  
  
     Si noti che il testo deve essere presente nel **percorso di pubblicazione** casella affinché il pulsante Sfoglia (**...** ) funzionamento del pulsante.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



