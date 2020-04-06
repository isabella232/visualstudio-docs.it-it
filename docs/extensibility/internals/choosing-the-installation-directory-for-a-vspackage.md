---
title: Scelta della directory di installazione per un pacchetto VSPackage Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8391cbdd3a857ea4ebaf3a36655520935f1a128
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709766"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Scegliere la directory di installazione per un pacchetto VSPackageChoose the installation directory for a VSPackage
Un pacchetto VSPackage e i relativi file di supporto devono essere nel file system di un utente. Il percorso dipende dal fatto che il pacchetto VSPackage è gestito o non gestito, lo schema di controllo delle versioni side-by-side e la scelta dell'utente.

## <a name="unmanaged-vspackages"></a>VSPackage non gestitiUnmanaged VSPackages
 Un VSPackage non gestito è un server COM che può essere installato in qualsiasi posizione. Le sue informazioni di registrazione devono riflettere accuratamente la sua posizione. L'interfaccia utente del programma di installazione deve fornire `ProgramFilesFolder` un percorso predefinito come sottodirectory del valore della proprietà di Windows Installer. Ad esempio:

*&lt;ProgramFilesFolder&gt;\\&lt;&gt;\\&lt;MyCompany ProdottoPacchettoPacchettiProdotto&gt;V1.0\\*

 L'utente dovrebbe essere autorizzato a modificare la directory predefinita per ospitare gli utenti che mantengono una piccola partizione di avvio e preferiscono installare applicazioni e strumenti su un altro volume.

 Se lo schema side-by-side utilizza un VSPackage con controllo delle versioni, è possibile utilizzare le sottodirectory per archiviare versioni diverse. Ad esempio:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>VSPackage gestiti
 VSPackage gestiti possono anche essere installati in qualsiasi posizione. Tuttavia, è consigliabile installarli sempre nella Global Assembly Cache (GAC) per ridurre i tempi di caricamento dell'assembly. Poiché i package VS gestiti sono sempre assembly con nome sicuro, installarli nella Global Assembly Cache significa che la verifica della firma con nome sicuro richiede solo al momento dell'installazione. Gli assembly con nome sicuro installati altrove nel file system devono avere le firme verificate ogni volta che vengono caricati. Quando si installa VSPackage gestiti nella Global Assembly Cache, utilizzare l'opzione **/assembly** dello strumento regpkg per scrivere voci del Registro di sistema che puntano al nome sicuro dell'assembly.

 Se si installano VSPackage gestiti in un percorso diverso dalla Global Assembly Cache, seguire i consigli precedenti forniti per i package VS non gestiti per la scelta delle gerarchie di directory. Utilizzare l'opzione **/codebase** dello strumento regpkg per scrivere voci del Registro di sistema che puntano al percorso dell'assembly VSPackage.

 Per ulteriori informazioni, vedere [Registrare e annullare la registrazione](../../extensibility/registering-and-unregistering-vspackages.md)di VSPackage .

## <a name="satellite-dlls"></a>DLL satellite
 Per convenzione, le DLL satellite VSPackage, che contengono le risorse per determinate impostazioni locali, si trovano nelle sottodirectory della directory *VSPackage.* Le sottodirectory corrispondono ai valori dell'ID delle impostazioni locali (LCID).

 L'articolo [Gestisci VSPackage](../../extensibility/managing-vspackages.md) indica che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le voci del Registro di sistema controllano dove cerca effettivamente la DLL satellite di un VSPackage. Tuttavia, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta di caricare una DLL satellite in una sottodirectory denominata per un valore LCID, nel seguente ordine:

1. LCID predefinito (LCID di Visual Studio, ad esempio, *1033* per l'inglese)

2. LCID predefinito con la sottolingua predefinita.

3. LCID predefinito del sistema.

4. LCID predefinito del sistema con la sottolingua predefinita.

5. Inglese (in inglese) ( . . *.\0x409*. .*.* . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

Se la DLL VSPackage include risorse e la voce del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Registro di sistema **SatelliteDll DllName** vi punta, tenta di caricarli nell'ordine precedente.

## <a name="see-also"></a>Vedere anche
- [Scegliere tra package VS condivisi e con controllo delle versioni](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Gestire VSPackage](../../extensibility/managing-vspackages.md)
- [Gestire la registrazione dei pacchetti](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
