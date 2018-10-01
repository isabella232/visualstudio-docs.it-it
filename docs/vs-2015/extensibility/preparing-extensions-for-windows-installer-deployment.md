---
title: Preparazione di estensioni per la distribuzione di Windows Installer | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b83e7d59e17b91e3a47625917de4ec7366f8389d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526698"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Preparazione di estensioni per la distribuzione di Windows Installer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [preparazione di estensioni per Windows Installer distribuzione](https://docs.microsoft.com/visualstudio/extensibility/preparing-extensions-for-windows-installer-deployment).  
  
È possibile utilizzare un pacchetto di Windows Installer (MSI) per distribuire un pacchetto VSIX. Tuttavia, è possibile estrarre il contenuto di un pacchetto VSIX per la distribuzione di file MSI. Questo documento illustra come preparare un progetto di cui l'output predefinito è un pacchetto VSIX per l'inclusione in un progetto di installazione.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Preparazione di un progetto di estensione per la distribuzione di Windows Installer  
 Eseguire questi passaggi in nuovi progetti di estensione prima di aggiungere a un progetto di installazione.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Per preparare un progetto di estensione per la distribuzione di Windows Installer  
  
1.  Creare un pacchetto VSPackage, del componente MEF, dell'area di controllo dell'Editor o altro tipo di progetto di estendibilità che include un manifesto VSIX.  
  
2.  Aprire il manifesto VSIX nell'editor del codice.  
  
3.  Impostare l'elemento InstalledByMsi del manifesto VSIX per `true`. Per altre informazioni sul manifesto VSIX, vedere [riferimenti su VSIX Extension Schema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Ciò impedisce che il programma di installazione VSIX provi a installare il componente.  
  
4.  Fare clic sul progetto in **Esplora soluzioni** e fare clic su **proprietà**.  
  
5.  Selezionare il **VSIX** scheda.  
  
6.  Selezionare la casella **contenuto VSIX copia nel percorso seguente** e digitare il percorso in cui il progetto di installazione verrà prelevati i file.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>L'estrazione dei file da un pacchetto VSIX esistente  
 Eseguire questi passaggi per aggiungere il contenuto di un pacchetto VSIX esistente a un progetto di installazione quando non è i file di origine.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Estrarre i file da un pacchetto VSIX esistente  
  
1.  Rinominare il. File VSIX che contiene l'estensione dal *nomefile*VSIX a *filename*con estensione zip.  
  
2.  Copiare il contenuto del file con estensione zip in una directory.  
  
3.  Eliminare il file [Content_types] XML dalla directory.  
  
4.  Modificare il manifesto VSIX, come illustrato nella procedura precedente.  
  
5.  Aggiungere i file rimanenti al progetto di installazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di programma di installazione di Visual Studio](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Procedura dettagliata: Creazione di un'azione personalizzata](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)

