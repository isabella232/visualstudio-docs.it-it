---
title: Scelta della directory di installazione per un pacchetto VSPackage | Microsoft Docs
description: Informazioni su come scegliere la directory di installazione per un PACCHETTO VSPackage e i relativi file di supporto, usando fattori quali se è gestito o non gestito.
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
ms.openlocfilehash: bde953b023b91c3c3e3b06fb3d50770851352da9d441b6277406ed91bbc392a5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359728"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Scegliere la directory di installazione per un pacchetto VSPackage
Un PACCHETTO VSPackage e i relativi file di supporto devono essere nel file system. Il percorso dipende dal fatto che il pacchetto VSPackage sia gestito o non gestito, dallo schema di controllo delle versioni side-by-side e dalla scelta dell'utente.

## <a name="unmanaged-vspackages"></a>Pacchetti VSPackage non gestiti
 Un VSPackage non gestito è un server COM che può essere installato in qualsiasi percorso. Le informazioni di registrazione devono riflettere in modo accurato la posizione. L'interfaccia utente del programma di installazione deve fornire un percorso predefinito come sottodirectory del `ProgramFilesFolder` valore della Windows Installer. Esempio:

*&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \V1.0\\*

 L'utente deve essere autorizzato a modificare la directory predefinita per contenere gli utenti che mantengono una partizione di avvio di piccole dimensioni e preferiscono installare applicazioni e strumenti in un altro volume.

 Se lo schema side-by-side usa un PACCHETTO VSPackage con versione, è possibile usare sottodirectory per archiviare versioni diverse. Esempio:

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ V1.0 \\ 2002\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ V1.0 \\ 2003\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ V1.0 \\ 2005\\*

## <a name="managed-vspackages"></a>VSPackage gestiti
 I pacchetti VSPackage gestiti possono anche essere installati in qualsiasi percorso. Tuttavia, è consigliabile installarli sempre nella Global Assembly Cache (GAC) per ridurre i tempi di caricamento degli assembly. Poiché i PACCHETTI VSPackage gestiti sono sempre assembly con nome sicuro, installandoli nella GAC significa che la verifica della firma con nome sicuro richiede solo in fase di installazione. Gli assembly con nome sicuro installati altrove nel file system devono avere le firme verificate ogni volta che vengono caricati. Quando si installano pacchetti VSPackage gestiti nella GAC, usare l'opzione **/assembly** dello strumento regpkg per scrivere voci del Registro di sistema che puntano al nome sicuro dell'assembly.

 Se si installano pacchetti VSPackage gestiti in un percorso diverso dalla GAC, seguire i suggerimenti precedenti per i pacchetti VSPackage non gestiti per la scelta delle gerarchie di directory. Usare l'opzione **/codebase** dello strumento regpkg per scrivere voci del Registro di sistema che puntano al percorso dell'assembly VSPackage.

 Per altre informazioni, vedere [Registrare e annullare la registrazione di pacchetti VSPackage.](../../extensibility/registering-and-unregistering-vspackages.md)

## <a name="satellite-dlls"></a>DLL satellite
 Per convenzione, le DLL satellite VSPackage, che contengono risorse per impostazioni locali specifiche, si trovano nelle sottodirectory della directory *VSPackage.* Le sottodirectory corrispondono ai valori dell'ID delle impostazioni locali (LCID).

 [L'articolo Gestire vspackage](../../extensibility/managing-vspackages.md) indica che le voci del Registro di sistema controllano dove cerca effettivamente la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DLL satellite di un VSPackage. Tuttavia, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta di caricare una DLL satellite in una sottodirectory denominata per un valore LCID, nell'ordine seguente:

1. LCID predefinito (Visual Studio LCID, ad esempio *\1033* per l'inglese)

2. LCID predefinito con la sottolinguaggio predefinita.

3. LCID predefinito del sistema.

4. LCID predefinito di sistema con la sottolinguaggio predefinita.

5. Inglese Stati Uniti (*.\1033* o *.\0x409*).

Se la DLL VSPackage include risorse e la voce del Registro di sistema **SatelliteDll\DllName** vi punta, tenta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di caricarle nell'ordine precedente.

## <a name="see-also"></a>Vedi anche
- [Scegliere tra pacchetti VSPackage condivisi e con versione](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Gestire VSPackage](../../extensibility/managing-vspackages.md)
- [Gestire la registrazione dei pacchetti](/previous-versions/bb166783(v=vs.100))