---
title: Scelta della directory di installazione per un pacchetto VSPackage | Microsoft Docs
description: Informazioni su come scegliere la directory di installazione per un pacchetto VSPackage e i relativi file di supporto, usando fattori come la gestione o l'non gestione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1a8b90fb00bed1e27a974924b07a5ddbc78dd37c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627347"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Scegliere la directory di installazione per un pacchetto VSPackage
Un VSPackage e i relativi file di supporto devono essere nel file system. Il percorso dipende dal fatto che il pacchetto VSPackage sia gestito o non gestito, dallo schema di controllo delle versioni side-by-side e dalla scelta dell'utente.

## <a name="unmanaged-vspackages"></a>VSPackage non gestiti
 Un VSPackage non gestito è un server COM che può essere installato in qualsiasi posizione. Le informazioni di registrazione devono riflettere in modo accurato la posizione. L'interfaccia utente del programma di installazione deve fornire un percorso predefinito come sottodirectory del valore della proprietà `ProgramFilesFolder` Windows Installer. Ad esempio:

*&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \V1.0\\*

 All'utente deve essere consentito modificare la directory predefinita per consentire agli utenti che mantengono una partizione di avvio di piccole dimensioni e preferiscono installare applicazioni e strumenti in un altro volume.

 Se lo schema side-by-side usa un VSPackage con versione, è possibile usare le sottodirectory per archiviare versioni diverse. Ad esempio:

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ V1.0 \\ 2002\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ V1.0 \\ 2003\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ V1.0 \\ 2005\\*

## <a name="managed-vspackages"></a>VSPackage gestiti
 I pacchetti VSPackage gestiti possono anche essere installati in qualsiasi posizione. Tuttavia, è consigliabile installarli sempre nella Global Assembly Cache (GAC) per ridurre i tempi di caricamento degli assembly. Poiché i pacchetti VSPackage gestiti sono sempre assembly con nome sicuro, installarli nella Global Assembly Cache significa che la verifica della firma con nome sicuro richiede solo in fase di installazione. Gli assembly con nome sicuro installati altrove nel file system devono avere le firme verificate ogni volta che vengono caricati. Quando si installano VSPackage gestiti nella GaC, usare l'opzione **/assembly** dello strumento regpkg per scrivere voci del Registro di sistema che puntano al nome sicuro dell'assembly.

 Se si installano VSPackage gestiti in un percorso diverso dalla GaC, seguire i consigli precedenti per i VSPackage non gestiti per la scelta delle gerarchie di directory. Usare l'opzione **/codebase** dello strumento regpkg per scrivere voci del Registro di sistema che puntano al percorso dell'assembly VSPackage.

 Per altre informazioni, vedere [Registrare e annullare la registrazione di VSPackage.](../../extensibility/registering-and-unregistering-vspackages.md)

## <a name="satellite-dlls"></a>DLL satellite
 Per convenzione, le DLL satellite VSPackage, che contengono risorse per determinate impostazioni locali, si trovano nelle sottodirectory della directory *VSPackage.* Le sottodirectory corrispondono ai valori dell'ID delle impostazioni locali (LCID).

 [L'articolo Manage VSPackages](../../extensibility/managing-vspackages.md) (Gestisci VSPackages) indica che le voci del Registro di sistema controllano dove [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] effettivamente cerca la DLL satellite di un VSPackage. Tenta tuttavia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di caricare una DLL satellite in una sottodirectory denominata per un valore LCID, nell'ordine seguente:

1. LCID predefinito (Visual Studio LCID, ad esempio *\1033 per* l'inglese)

2. LCID predefinito con la sottolingua predefinita.

3. LCID predefinito del sistema.

4. LCID predefinito del sistema con la sottolingua predefinita.

5. Inglese Stati Uniti (*.\1033* o *.\0x409*).

Se la DLL VSPackage include risorse e la voce del Registro di sistema **SatelliteDll\DllName** vi punta, tenta di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caricarle nell'ordine precedente.

## <a name="see-also"></a>Vedi anche
- [Scegliere tra vspackage condivisi e con controllo delle versioni](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Gestire VSPackage](../../extensibility/managing-vspackages.md)
- [Gestire la registrazione dei pacchetti](/previous-versions/bb166783(v=vs.100))