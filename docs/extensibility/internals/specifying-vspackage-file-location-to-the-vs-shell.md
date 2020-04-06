---
title: Specifica del percorso del file VSPackage per la shell di VS Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704974"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Definizione del percorso di file VSPackage nella shell di Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]deve essere in grado di individuare la DLL dell'assembly per caricare il pacchetto VSPackage. È possibile individuarlo in vari modi, come descritto nella tabella seguente.

| Metodo | Descrizione |
| - | - |
| Utilizzare la chiave del Registro di sistema CodeBase. | Il CodeBase chiave può [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] essere utilizzata per indirizzare a caricare l'assembly VSPackage da qualsiasi percorso di file completo. Il valore della chiave deve essere il percorso del file della DLL. Questo è il modo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] migliore per caricare l'assieme del pacchetto. Questa tecnica viene talvolta definita "CodeBase/tecnica della directory di installazione privata". Durante la registrazione il valore della codebase viene passato alle <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> classi di attributi di registrazione tramite un'istanza del tipo. |
| Inserire la DLL nella directory **PrivateAssemblies.** | Inserire l'assembly nella sottodirectory [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **PrivateAssemblies** della directory. Gli assembly che si trovano in **PrivateAssemblies** vengono rilevati automaticamente, ma non sono visibili nella finestra di dialogo **Aggiungi riferimenti.** La differenza tra **PrivateAssemblies** e **PublicAssemblies** consiste nel fatto che gli assembly in **PublicAssemblies** vengono enumerati nella finestra di dialogo **Aggiungi riferimenti.** Se si è scelto di non utilizzare la tecnica "CodeBase/private installation directory", è necessario eseguire l'installazione nella directory **PrivateAssemblies.** |
| Utilizzare un assembly con nome sicuro e la chiave del Registro di sistema Assembly. | Il Assembly chiave può essere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzata per indirizzare in modo esplicito per caricare un assembly VSPackage con nome sicuro. Il valore della chiave deve essere il nome sicuro dell'assembly. |
| Inserire la DLL nella directory **PublicAssemblies.** | Infine, l'assembly può essere inserito anche nella sottodirectory **PublicAssemblies.** Gli assembly che si trovano in **PublicAssemblies** vengono rilevati [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]automaticamente e verranno visualizzati anche nella finestra di dialogo Aggiungi **riferimenti** in .<br /><br /> Gli assembly VSPackage devono essere inseriti nella directory PublicAssemblies solo se contengono componenti gestiti che devono essere riutilizzati da altri sviluppatori VSPackage.VSPackage assemblies should only be placed in the **PublicAssemblies** directory if they contain managed components that are intended to be reused by other VSPackage developers. La maggior parte delle assemblee non soddisfa questo criterio. |

> [!NOTE]
> Utilizzare assembly firmati con nome sicuro per tutti gli assembly dipendenti. Questi assembly devono inoltre essere installati nella propria directory o nella Global Assembly Cache (GAC). In questo modo si protegge da conflitti con assembly con lo stesso nome di file di base, noto come associazione di nomi deboli.
