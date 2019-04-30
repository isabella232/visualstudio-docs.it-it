---
title: 'Procedura: Specificare i file in cui le copie di Visual Studio 2015 | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 5d36c5dafa37673263ab13dc46c7f02e44448fd8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441625"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Procedura: Specificare il percorso in cui vengono copiati i file in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si pubblica un'applicazione tramite ClickOnce, la proprietà `Publish Location` specifica il percorso in cui vengono inseriti i file dell'applicazione e il manifesto. Può trattarsi di un percorso di file o del percorso di un server FTP.

 È possibile specificare la proprietà `Publish Location` nella pagina **Pubblica** di **Progettazione progetti** oppure mediante la Pubblicazione guidata. Per altre informazioni, vedere [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.

### <a name="to-specify-a-publishing-location"></a>Per specificare un percorso di pubblicazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Nel campo **Percorso pubblicazione** immettere il percorso di pubblicazione usando uno dei formati seguenti:

   - Per pubblicare in un percorso di condivisione o un disco del file, immettere il percorso utilizzando un percorso UNC (\\\Server\ApplicationName) o un percorso di file (C:\Deploy\ApplicationName).

   - Per pubblicare in un server FTP, immettere il percorso nel formato ftp://ftp.microsoft.com/NomeApplicazione.

     Si noti che il testo deve essere presente nella casella **Posizione di pubblicazione** perché il pulsante Sfoglia (**...**) funzioni.

## <a name="see-also"></a>Vedere anche
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md) [come: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
