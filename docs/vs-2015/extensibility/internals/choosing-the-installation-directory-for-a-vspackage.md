---
title: Scegliere la Directory di installazione per un pacchetto VSPackage | Microsoft Docs
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
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ebe7ce3855b2d91687251176dc3dd5acd4c7ad2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525450"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Scelta della directory di installazione per un pacchetto VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [scegliendo la Directory di installazione per un pacchetto VSPackage](https://docs.microsoft.com/visualstudio/extensibility/internals/choosing-the-installation-directory-for-a-vspackage).  
  
Un pacchetto VSPackage e relativi file di supporto devono trovarsi nel file system dell'utente. Il percorso dipende se il pacchetto VSPackage gestito o non gestiti, il regime di controllo delle versioni side-by-side e scelta dell'utente.  
  
## <a name="unmanaged-vspackages"></a>Pacchetti VSPackage non gestiti  
 Un VSPackage non gestito è un server COM che può essere installato in qualsiasi posizione. Le informazioni di registrazione deve riflette accuratamente la posizione. Interfaccia utente (UI) programma di installazione deve fornire un percorso predefinito come una sottodirectory della proprietà ProgramFilesFolder Windows Installer. Ad esempio:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 L'utente deve essere autorizzato a modificare la directory predefinita per le esigenze degli utenti che dispongono di una partizione di avvio di piccole dimensioni e si preferisce installare strumenti e applicazioni in un altro volume.  
  
 Se un pacchetto VSPackage con controllo delle versioni è usato dallo schema di side-by-side, è possibile utilizzare le sottodirectory per archiviare versioni diverse. Ad esempio:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>VSPackage gestiti  
 Pacchetti VSPackage gestiti possono anche essere installati in qualsiasi posizione. Tuttavia, è consigliabile eseguirne l'installazione sempre alla global assembly cache (GAC) per ridurre i tempi di caricamento di assembly. Poiché i pacchetti VSPackage gestiti sono sempre assembly con nome sicuro, installarli nella Global Assembly Cache significa che la verifica delle firme con nome sicuro richiede solo al momento dell'installazione. Gli assembly con nome sicuro installati in un' posizione nel file system devono avere le relative firme verificate ogni volta che sono stati caricati. Quando si installano pacchetti VSPackage gestiti nella Global Assembly Cache, utilizzare lo strumento regpkg **/assembly** switch per scrivere le voci del Registro di sistema che punta al nome sicuro dell'assembly.  
  
 Se si installano pacchetti VSPackage gestiti in un percorso diverso dalla Global Assembly Cache, seguire il Consiglio precedente specificato per i pacchetti VSPackage non gestiti per la scelta delle gerarchie di directory. Utilizzare lo strumento regpkg **/codebase** switch per scrivere le voci del Registro di sistema che punta al percorso dell'assembly VSPackage.  
  
 Per altre informazioni, vedere [la registrazione e annullamento della registrazione dei pacchetti VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>DLL satellite  
 Per convenzione, DLL satellite di VSPackage, che contengono le risorse per determinate impostazioni locali, ovvero si trovano nella sottodirectory della directory di VSPackage. Le sottodirectory corrispondano ai valori di ID (LCID) delle impostazioni locali.  
  
 [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md) indica che le voci del Registro di sistema consentono di controllare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] effettivamente Cerca un pacchetto VSPackage satellite DLL. Tuttavia, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tenta di caricare una DLL satellite in una sottodirectory denominata per un valore LCID, nell'ordine seguente:  
  
1.  LCID (LCID di Visual Studio, ad esempio \1033 per inglese) predefinito  
  
2.  Identificatore LCID predefinito con la varietà di lingua predefinita.  
  
3.  Identificatore LCID predefinito di sistema.  
  
4.  Sistema LCID predefinito con la varietà di lingua predefinita.  
  
5.  STATI UNITI Inglese (. \1033 o. \0x409).  
  
 Se la DLL VSPackage include risorse e i punti di ingresso SatelliteDll\DllName del Registro di sistema, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tenta di caricarli nell'ordine sopra indicato.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta tra pacchetti VSPackage condivisi e con controllo delle versioni](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)   
 [Registrazione del pacchetto gestito](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)

