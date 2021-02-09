---
title: Scelta della directory di installazione per un pacchetto VSPackage | Microsoft Docs
description: Informazioni su come scegliere la directory di installazione per un pacchetto VSPackage e i relativi file di supporto, usando fattori quali, ad esempio, se sono gestiti o non gestiti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea697e6e445eeae117bb6bf1d1603220ec0c0675
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874074"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Scegliere la directory di installazione per un pacchetto VSPackage
Un pacchetto VSPackage e i relativi file di supporto devono trovarsi nel file system di un utente. Il percorso varia a seconda che il pacchetto VSPackage sia gestito o non gestito, lo schema di controllo delle versioni side-by-side e la scelta dell'utente.

## <a name="unmanaged-vspackages"></a>Pacchetti VSPackage non gestiti
 Un pacchetto VSPackage non gestito è un server COM che può essere installato in qualsiasi percorso. Le informazioni di registrazione devono riflettere accuratamente la relativa posizione. L'interfaccia utente del programma di installazione deve fornire un percorso predefinito come sottodirectory del valore della `ProgramFilesFolder` proprietà Windows Installer. Ad esempio:

*&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \v1.0\\*

 L'utente deve essere autorizzato a modificare la directory predefinita per consentire agli utenti che conservano una partizione di avvio ridotta e preferiscono installare applicazioni e strumenti in un altro volume.

 Se lo schema side-by-side usa un pacchetto VSPackage con versione, è possibile usare le sottodirectory per archiviare versioni diverse. Ad esempio:

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ v 1.0 \\ 2002\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ v 1.0 \\ 2003\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ v 1.0 \\ 2005\\*

## <a name="managed-vspackages"></a>VSPackage gestiti
 I pacchetti VSPackage gestiti possono essere installati anche in qualsiasi posizione. Tuttavia, è consigliabile installarli sempre nella Global Assembly Cache (GAC) per ridurre i tempi di caricamento degli assembly. Poiché i pacchetti VSPackage gestiti sono sempre assembly con nome sicuro, l'installazione nella GAC significa che la verifica della firma con nome sicuro accetta solo al momento dell'installazione. Gli assembly con nome sicuro installati altrove nel file system devono avere le firme verificate ogni volta che vengono caricati. Quando si installa VSPackage gestiti nella GAC, usare l'opzione **/assembly** dello strumento regpkg per scrivere le voci del registro di sistema che puntano al nome sicuro dell'assembly.

 Se si installa VSPackage gestiti in un percorso diverso dalla GAC, seguire le indicazioni precedenti fornite per i pacchetti VSPackage non gestiti per la scelta delle gerarchie di directory. Usare l'opzione **/codebase** dello strumento regpkg per scrivere voci del registro di sistema che puntano al percorso dell'assembly VSPackage.

 Per altre informazioni, vedere [registrare e annullare la registrazione di pacchetti VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>DLL satellite
 Per convenzione, le DLL satellite VSPackage, che contengono risorse per determinate impostazioni locali, si trovano in sottodirectory della directory *VSPackage* . Le sottodirectory corrispondono ai valori dell'ID delle impostazioni locali (LCID).

 L'articolo [gestire i pacchetti VSPackage](../../extensibility/managing-vspackages.md) indica che le voci del registro di sistema controllano dove [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Cerca effettivamente la DLL satellite del pacchetto VSPackage. Tuttavia, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta di caricare una DLL satellite in una sottodirectory denominata per un valore LCID, nell'ordine seguente:

1. LCID predefinito (LCID di Visual Studio, ad esempio *\ 1033* per l'inglese)

2. LCID predefinito con la lingua predefinita.

3. LCID predefinito del sistema.

4. LCID predefinito del sistema con la lingua predefinita.

5. Inglese Stati Uniti (*. \ 1033* o *.\0x409*).

Se la DLL del pacchetto VSPackage include risorse e i punti di ingresso del registro di sistema **SatelliteDll\DllName** , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta di caricarli nell'ordine precedente.

## <a name="see-also"></a>Vedi anche
- [Scegliere tra VSPackage condivisi e con versione](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Gestire VSPackage](../../extensibility/managing-vspackages.md)
- [Gestire la registrazione del pacchetto](/previous-versions/bb166783(v=vs.100))