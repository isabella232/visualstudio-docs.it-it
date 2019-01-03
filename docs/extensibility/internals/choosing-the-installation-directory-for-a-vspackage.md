---
title: Scegliere la Directory di installazione per un pacchetto VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df13749a16ad107c864fa1dcf1b3e0f4e7cbed41
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926294"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Scegliere la directory di installazione per un pacchetto VSPackage
Un pacchetto VSPackage e relativi file di supporto devono trovarsi nel file system dell'utente. Il percorso dipende se il pacchetto VSPackage gestito o non gestiti, il regime di controllo delle versioni side-by-side e scelta dell'utente.  
  
## <a name="unmanaged-vspackages"></a>Pacchetti VSPackage non gestiti  
 Un VSPackage non gestito è un server COM che può essere installato in qualsiasi posizione. Le informazioni di registrazione devono riflettere accuratamente la posizione. Interfaccia utente (UI) programma di installazione deve fornire un percorso predefinito come sottodirectory del `ProgramFilesFolder` valore della proprietà Windows Installer. Ad esempio:  
  
*&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\V1.0\\*
  
 L'utente deve essere autorizzato a modificare la directory predefinita per le esigenze degli utenti che dispongono di una partizione di avvio di piccole dimensioni e si preferisce installare strumenti e applicazioni in un altro volume.  
  
 Se un pacchetto VSPackage con controllo delle versioni è usato dallo schema di side-by-side, è possibile utilizzare le sottodirectory per archiviare versioni diverse. Ad esempio:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*
  
 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*
  
 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*
  
## <a name="managed-vspackages"></a>VSPackage gestiti  
 Pacchetti VSPackage gestiti possono anche essere installati in qualsiasi posizione. Tuttavia, è consigliabile eseguirne l'installazione sempre alla global assembly cache (GAC) per ridurre i tempi di caricamento di assembly. Poiché i pacchetti VSPackage gestiti sono sempre assembly con nome sicuro, installarli nella Global Assembly Cache significa che la verifica delle firme con nome sicuro richiede solo al momento dell'installazione. Gli assembly con nome sicuro installati in un' posizione nel file system devono avere le relative firme verificate ogni volta che sono stati caricati. Quando si installano pacchetti VSPackage gestiti nella Global Assembly Cache, utilizzare lo strumento regpkg **/assembly** switch per scrivere le voci del Registro di sistema che punta al nome sicuro dell'assembly.  
  
 Se si installano pacchetti VSPackage gestiti in un percorso diverso dalla Global Assembly Cache, seguire il Consiglio precedente specificato per i pacchetti VSPackage non gestiti per la scelta delle gerarchie di directory. Utilizzare lo strumento regpkg **/codebase** switch per scrivere le voci del Registro di sistema che punta al percorso dell'assembly VSPackage.  
  
 Per altre informazioni, vedere [registrare e annullare la registrazione di pacchetti VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>DLL satellite  
 Per convenzione, DLL, che contengono le risorse di determinate impostazioni locali, satellite presenti nelle sottodirectory di VSPackage la *VSPackage* directory. Le sottodirectory corrispondano ai valori di ID (LCID) delle impostazioni locali.  
  
 Il [gestire i pacchetti VSPackage](../../extensibility/managing-vspackages.md) articolo indica che le voci del Registro di sistema consentono di controllare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] effettivamente Cerca un pacchetto VSPackage satellite DLL. Tuttavia, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta di caricare una DLL satellite in una sottodirectory denominata per un valore LCID, nell'ordine seguente:  
  
1.  Default LCID (identificatore LCID di Visual Studio, ad esempio *\1033* per la lingua inglese)  
  
2.  Identificatore LCID predefinito con la varietà di lingua predefinita.  
  
3.  Identificatore LCID predefinito di sistema.  
  
4.  Sistema LCID predefinito con la varietà di lingua predefinita.  
  
5.  STATI UNITI Inglese (*. \1033* oppure *. \0x409*).  
  

Se la DLL VSPackage contiene delle risorse e il **SatelliteDll\DllName** voce del Registro di sistema fa riferimento ad esso, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta di caricarli nell'ordine sopra indicato.  
  
## <a name="see-also"></a>Vedere anche  
 [Scegliere tra pacchetti VSPackage condivisi e con controllo delle versioni](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Gestire i pacchetti VSPackage](../../extensibility/managing-vspackages.md)   
 [Gestire la registrazione del pacchetto](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)