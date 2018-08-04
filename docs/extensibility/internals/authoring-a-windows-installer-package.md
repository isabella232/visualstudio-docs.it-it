---
title: Creazione di un pacchetto di programma di installazione di Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: edb0a1d385129600372fc26693aec729751a768c
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512868"
---
# <a name="author-a-windows-installer-package"></a>Creare un pacchetto Windows Installer
Il modello di Windows Installer le unità di dati. Anziché scrivere uno script contenente le procedure per copiare i file e scrivere le voci del Registro di sistema, ad esempio, si creano righe e colonne nelle tabelle di database che contengono dati di file e Registro di sistema.  
  
## <a name="database-entries"></a>Voci di database  
Per installare un pacchetto VSPackage, un pacchetto Windows Installer deve contenere le voci del database per eseguire le attività seguenti:  
  
- Eseguire la ricerca del sistema per individuare le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta il pacchetto VSPackage (usando le tabelle di Windows Installer che includono AppSearch CompLocator, RegLocator, DrLocator e firma).  
  
- Annullare l'installazione se nessuna versione supportata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è installato o se un altro requisito di sistema del pacchetto VSPackage non viene soddisfatta (usando la tabella LaunchCondition).  
  
- Installare il pacchetto VSPackage e i file dipendenti (utilizzando la directory, componenti e le tabelle file).  
  
- Aggiungere le informazioni appropriate per il pacchetto VSPackage nel Registro di sistema (usando la tabella del Registro di sistema).  
  
- Integrare il pacchetto VSPackage nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiamando **/setup devenv.exe** (usando la tabella CustomAction).  
  
Per altre informazioni, vedere [Windows Installer](/windows/desktop/Msi/windows-installer-portal).
  
## <a name="setup-tools"></a>Strumenti di installazione  
Un'ampia gamma di strumenti di installazione di terze parti offrono un ambiente di sviluppo per pacchetti di Windows Installer. I seguenti strumenti gratuiti sono disponibili:  
  
- InstallShield limited edition  
  
   È possibile ottenere una versione limitata di InstallShield tramite Visual Studio **nuovo progetto** finestra di dialogo. Espandere **altri tipi di progetto** e quindi selezionare **il programma di installazione e distribuzione**. Selezionare il modello di InstallShield.  
  
- Set di strumenti Windows Installer XML  
  
   Il set di strumenti di Windows Installer XML (WiX) compila i pacchetti di Windows Installer dai file di origine XML. Il set di strumenti WiX è un progetto open source di Microsoft. È possibile scaricare il codice sorgente e file eseguibili da [set di strumenti Wix](http://sourceforge.net/projects/wix).  
  
   Per i prodotti commerciali integrano [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usando il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], vedere [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Vedere anche  
 [Installare i pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)