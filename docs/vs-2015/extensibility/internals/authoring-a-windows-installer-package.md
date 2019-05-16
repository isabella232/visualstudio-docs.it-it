---
title: Creazione di un pacchetto di programma di installazione di Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e92e965f0efe531f1618be509d0a7c9655c573d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682544"
---
# <a name="authoring-a-windows-installer-package"></a>Creazione e modifica di un pacchetto di Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il modello di Windows Installer le unità di dati. Anziché scrivere uno script contenente le procedure per copiare i file e scrivere le voci del Registro di sistema, ad esempio, si creano righe e colonne nelle tabelle di database che contengono dati di file e Registro di sistema.  
  
## <a name="database-entries"></a>Voci di database  
 Per installare un pacchetto VSPackage, un pacchetto Windows Installer deve contenere le voci del database per eseguire le attività seguenti:  
  
- Eseguire la ricerca del sistema per individuare le versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporta il pacchetto VSPackage (usando le tabelle di Windows Installer che includono AppSearch CompLocator, RegLocator, DrLocator e firma).  
  
- Annullare l'installazione se nessuna versione supportata di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è installato o se un altro requisito di sistema del pacchetto VSPackage non viene soddisfatta (usando la tabella LaunchCondition).  
  
- Installare il pacchetto VSPackage e i file dipendenti (utilizzando la directory, componenti e le tabelle file).  
  
- Aggiungere le informazioni appropriate per il pacchetto VSPackage nel Registro di sistema (usando la tabella del Registro di sistema).  
  
- Integrare il pacchetto VSPackage nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] chiamando **/setup devenv.exe** (usando la tabella CustomAction).  
  
  Per altre informazioni, vedere [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Strumenti di installazione  
 Un'ampia gamma di strumenti di installazione di terze parti offrono un ambiente di sviluppo per pacchetti di Windows Installer. Due strumenti gratuiti sono i seguenti:  
  
- InstallShield Limited Edition  
  
   È possibile ottenere una versione limitata di InstallShield tramite Visual Studio **nuovo progetto** finestra di dialogo. Espandere **altri tipi di progetto** e quindi selezionare **il programma di installazione e distribuzione**. Selezionare il modello di InstallShield.  
  
- set di strumenti XML di Windows Installer  
  
   Il set di strumenti consente di compilare pacchetti di installazione di Windows dai file di origine XML. Il set di strumenti è un progetto open source di Microsoft. È possibile scaricare il codice sorgente e file eseguibili da [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
  Per i prodotti commerciali integrano [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usando il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], vedere [ https://marketplace.visualstudio.com/ ](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
