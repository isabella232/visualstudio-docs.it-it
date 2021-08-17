---
title: Specifica del percorso del file VSPackage nella shell vs | Microsoft Docs
description: Informazioni su come rendere possibile al Visual Studio individuare la DLL dell'assembly per caricare il pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 044655e6f1b1eb984e521b26cb9796ae3e5543d0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057161"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Definizione del percorso di file VSPackage nella shell di Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve essere in grado di individuare la DLL dell'assembly per caricare il pacchetto VSPackage. È possibile individuarlo in vari modi, come descritto nella tabella seguente.

| Metodo | Descrizione |
| - | - |
| Usare la chiave del Registro di sistema CodeBase. | La chiave CodeBase può essere usata per indirizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il caricamento dell'assembly VSPackage da qualsiasi percorso di file completo. Il valore della chiave deve essere il percorso del file della DLL. Questo è il modo migliore per caricare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'assembly del pacchetto. Questa tecnica viene talvolta definita "tecnica della directory di installazione CodeBase/privata". Durante la registrazione il valore della codebase viene passato alle classi di attributi di registrazione tramite un'istanza del <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> tipo . |
| Inserire la DLL nella directory **PrivateAssemblies.** | Inserire l'assembly **nella sottodirectory PrivateAssemblies** della [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directory . Gli assembly che si trovano in **PrivateAssemblies** vengono rilevati automaticamente, ma non sono visibili nella **finestra di dialogo** Aggiungi riferimenti . La differenza tra **PrivateAssemblies** **e PublicAssemblies** è che gli assembly in **PublicAssemblies** vengono enumerati nella **finestra di dialogo** Aggiungi riferimenti. Se si è scelto di non usare la tecnica "CodeBase/directory di installazione privata", è necessario eseguire l'installazione nella directory **PrivateAssemblies.** |
| Usare un assembly con nome sicuro e la chiave del Registro di sistema Assembly. | La chiave Assembly può essere usata per indirizzare in modo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] esplicito il caricamento di un assembly VSPackage con nome sicuro. Il valore della chiave deve essere il nome sicuro dell'assembly. |
| Inserire la DLL nella directory **PublicAssemblies.** | Infine, l'assembly può anche essere inserito nella **sottodirectory PublicAssemblies.** Gli assembly che si trovano in **PublicAssemblies** vengono rilevati automaticamente e verranno visualizzati anche nella finestra **di dialogo** Aggiungi riferimenti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .<br /><br /> Gli assembly VSPackage devono essere inseriti nella directory **PublicAssemblies** solo se contengono componenti gestiti che devono essere riutilizzati da altri sviluppatori VSPackage. La maggior parte degli assembly non soddisfa questo criterio. |

> [!NOTE]
> Usare assembly firmati con nome sicuro per tutti gli assembly dipendenti. Questi assembly devono essere installati anche nella propria directory o nella Global Assembly Cache (GAC). In questo modo è possibile evitare conflitti con assembly con lo stesso nome di file di base, noto come associazione con nome debole.
