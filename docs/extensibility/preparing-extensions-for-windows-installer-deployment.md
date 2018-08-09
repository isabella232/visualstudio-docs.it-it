---
title: Preparazione di estensioni per la distribuzione di Windows Installer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef69ac45a090aa4395aa15d1395cff1665255b51
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639113"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Preparare le estensioni per la distribuzione di Windows Installer
È possibile utilizzare un pacchetto di Windows Installer (MSI) per distribuire un pacchetto VSIX. Tuttavia, è possibile estrarre il contenuto di un pacchetto VSIX per la distribuzione di file MSI. Questo documento illustra come preparare un progetto di cui l'output predefinito è un pacchetto VSIX per l'inclusione in un progetto di installazione.  
  
## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Preparare un progetto di estensione per la distribuzione di Windows Installer  
 Eseguire questi passaggi in nuovi progetti di estensione prima di aggiungere a un progetto di installazione.  
  
### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Per preparare un progetto di estensione per la distribuzione di Windows Installer  
  
1.  Creare un pacchetto VSPackage, del componente MEF, dell'area di controllo dell'Editor o altro tipo di progetto di estendibilità che include un manifesto VSIX.  
  
2.  Aprire il manifesto VSIX nell'editor del codice.  
  
3.  Impostare il `InstalledByMsi` elemento del manifesto VSIX per `true`. Per altre informazioni sul manifesto VSIX, vedere [riferimenti su VSIX extension schema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Ciò impedisce che il programma di installazione VSIX provi a installare il componente.  
  
4.  Fare clic sul progetto in **Esplora soluzioni** e fare clic su **proprietà**.  
  
5.  Selezionare il **VSIX** scheda.  
  
6.  Selezionare la casella **contenuto VSIX copia nel percorso seguente** e digitare il percorso in cui il progetto di installazione verrà prelevati i file.  
  
## <a name="extract-files-from-an-existing-vsix-package"></a>Estrarre i file da un pacchetto VSIX esistente  
 Eseguire questi passaggi per aggiungere il contenuto di un pacchetto VSIX esistente a un progetto di installazione quando non è i file di origine.  
  
### <a name="to-extract-files-from-an-existing-vsix-package"></a>Estrarre i file da un pacchetto VSIX esistente  
  
1.  Rinominare il *. VSIX* contenente l'estensione dal file *filename.vsix* al *filename.zip*.  
  
2.  Copiare il contenuto del *zip* file in una directory.  
  
3.  Eliminare il *[Content_types] XML* file dalla directory.  
  
4.  Modificare il manifesto VSIX, come illustrato nella procedura precedente.  
  
5.  Aggiungere i file rimanenti al progetto di installazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione del programma di installazione Visual Studio](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Procedura dettagliata: Creare un'azione personalizzata](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)