---
title: Creazione di un pacchetto di Windows Installer | Microsoft Docs
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
ms.openlocfilehash: 58529dabbb52ceb751c67be24beb1d21285a1de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301140"
---
# <a name="authoring-a-windows-installer-package"></a>Creazione e modifica di un pacchetto di Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I dati guidano il modello di Windows Installer. Anziché scrivere uno script procedurale per copiare file e scrivere voci del registro di sistema, ad esempio, è possibile creare righe e colonne in tabelle di database che contengono dati di file e registro di sistema.  
  
## <a name="database-entries"></a>Voci di database  
 Per installare un pacchetto VSPackage, un pacchetto di Windows Installer deve contenere voci di database per eseguire le attività seguenti:  
  
- Eseguire una ricerca nel sistema per individuare le versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supportato da VSPackage (usando Windows Installer tabelle che includono AppSearch, CompLocator, RegLocator, DrLocator e Signature).  
  
- Annullare l'installazione se non è installata alcuna versione supportata di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o se non è stato soddisfatto un altro requisito di sistema del VSPackage (usando la tabella LaunchCondition).  
  
- Installare il pacchetto VSPackage e i file dipendenti (usando la directory, il componente e le tabelle di file).  
  
- Aggiungere le informazioni appropriate per il pacchetto VSPackage al registro di sistema (usando la tabella del registro di sistema).  
  
- Integrare il pacchetto VSPackage in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] chiamando **devenv. exe/Setup** (usando la tabella CustomAction).  
  
  Per ulteriori informazioni, vedere [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Strumenti di installazione  
 Un'ampia gamma di strumenti di installazione di terze parti fornisce un ambiente di sviluppo per i pacchetti Windows Installer. Di seguito sono riportati due strumenti gratuiti:  
  
- InstallShield Limited Edition  
  
   È possibile ottenere una versione limitata di InstallShield tramite la finestra di dialogo **nuovo progetto** di Visual Studio. Espandere **altri tipi di progetto** , quindi selezionare **installazione e distribuzione**. Selezionare il modello InstallShield.  
  
- set di strumenti XML di Windows Installer  
  
   Il set di strumenti compila Windows Installer pacchetti dai file di origine XML. Il set di strumenti è un progetto open source Microsoft. È possibile scaricare il codice sorgente e i file eseguibili da [http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/).  
  
  Per i prodotti commerciali che si integrano in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usando il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], vedere [https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
