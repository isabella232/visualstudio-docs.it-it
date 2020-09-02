---
title: Preparazione delle estensioni per la distribuzione di Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 76d7f879fade99914bf3f56ade0ec1270e14f4c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694599"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Preparazione di estensioni per la distribuzione di Windows Installer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Non è possibile usare un pacchetto di Windows Installer (MSI) per distribuire un pacchetto VSIX. Tuttavia, è possibile estrarre il contenuto di un pacchetto VSIX per la distribuzione di MSI. Questo documento illustra come preparare un progetto il cui output predefinito è un pacchetto VSIX da includere in un progetto di installazione.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Preparazione di un progetto di estensione per la distribuzione di Windows Installer  
 Eseguire questi passaggi nei nuovi progetti di estensione prima di aggiungere a un progetto di installazione.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Per preparare un progetto di estensione per la distribuzione di Windows Installer  
  
1. Creare un pacchetto VSPackage, un componente MEF, un'area di lavoro dell'editor o un altro tipo di progetto di estendibilità che include un manifesto VSIX.  
  
2. Aprire il manifesto VSIX nell'editor di codice.  
  
3. Impostare l'elemento InstalledByMsi del manifesto VSIX su `true` . Per altre informazioni sul manifesto VSIX, vedere [riferimento allo schema di estensione vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Ciò impedisce al programma di installazione VSIX di tentare di installare il componente.  
  
4. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Proprietà**.  
  
5. Selezionare la scheda **VSIX** .  
  
6. Selezionare la casella **copia contenuto VSIX nel percorso seguente** e digitare il percorso in cui il progetto di installazione selezionerà i file.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Estrazione di file da un pacchetto VSIX esistente  
 Eseguire questi passaggi per aggiungere il contenuto di un pacchetto VSIX esistente a un progetto di installazione quando non si dispone dei file di origine.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Per estrarre i file da un pacchetto VSIX esistente  
  
1. Rinominare il. File VSIX contenente l'estensione da *nomefile*. vsix a *filename*. zip.  
  
2. Copiare il contenuto del file con estensione zip in una directory.  
  
3. Eliminare il file [Content_types]. XML dalla directory.  
  
4. Modificare il manifesto VSIX, come illustrato nella procedura precedente.  
  
5. Aggiungere i file rimanenti al progetto di installazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione Programma di installazione di Visual Studio](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Procedura dettagliata: creazione di un'azione personalizzata](https://msdn.microsoft.com/4bd4b63a-2b91-431e-839c-5752443f0eaf)
