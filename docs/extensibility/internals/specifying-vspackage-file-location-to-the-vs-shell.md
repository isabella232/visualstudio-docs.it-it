---
title: Specifica del percorso del file VSPackage per la shell di Visual Studio | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704974"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Definizione del percorso di file VSPackage nella shell di Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve essere in grado di individuare la DLL dell'assembly per il caricamento del pacchetto VSPackage. È possibile individuarlo in diversi modi, come descritto nella tabella seguente.

| Metodo | Descrizione |
| - | - |
| Utilizzare la chiave del registro di sistema codebase. | La chiave CODEBASE può essere usata per indirizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il caricamento dell'assembly VSPackage da un percorso file completo. Il valore della chiave deve corrispondere al percorso del file della DLL. Questo è il modo migliore per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caricare l'assembly del pacchetto. Questa tecnica viene a volte definita "tecnica di directory di codebase/installazione privata". Durante la registrazione, il valore della codebase viene passato alle classi degli attributi di registrazione tramite un'istanza del <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> tipo. |
| Inserire la DLL nella directory **PrivateAssemblies** | Inserire l'assembly nella sottodirectory **PrivateAssemblies** della [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Directory. Gli assembly che si trovano in **PrivateAssemblies** vengono rilevati automaticamente, ma non sono visibili nella finestra di dialogo **Aggiungi riferimenti** . La differenza tra **PrivateAssemblies** e **PublicAssemblies** consiste nel fatto che gli assembly in **PublicAssemblies** vengono enumerati nella finestra di dialogo **Aggiungi riferimenti** . Se si sceglie di non usare la tecnica "directory codebase/directory di installazione privata", è necessario installare nella directory **PrivateAssemblies** |
| Usare un assembly con nome sicuro e la chiave del registro di sistema dell'assembly. | La chiave assembly può essere usata per indirizzare in modo esplicito il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caricamento di un assembly VSPackage con nome sicuro. Il valore della chiave deve corrispondere al nome sicuro dell'assembly. |
| Inserire la DLL nella directory **PublicAssemblies** | Infine, l'assembly può essere inserito anche nella sottodirectory **PublicAssemblies** . Gli assembly che si trovano in **PublicAssemblies** vengono automaticamente rilevati e verranno visualizzati anche nella finestra di dialogo **Aggiungi riferimenti** in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .<br /><br /> Gli assembly VSPackage devono essere posizionati nella directory **PublicAssemblies** solo se contengono componenti gestiti destinati a essere riutilizzati da altri sviluppatori VSPackage. La maggior parte degli assembly non soddisfa questo criterio. |

> [!NOTE]
> Usare assembly firmati con nome sicuro per tutti gli assembly dipendenti. Questi assembly devono inoltre essere installati nella propria directory o nel Global Assembly Cache (GAC). In questo modo si evitano conflitti con gli assembly con lo stesso nome file di base, noto come binding con nome debole.
