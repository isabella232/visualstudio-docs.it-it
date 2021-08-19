---
title: Procedure consigliate per la sicurezza nei pacchetti VSPackage | Microsoft Docs
description: Informazioni sulle procedure consigliate per la sicurezza in un pacchetto VSPackage, l'unità di base di sicurezza e distribuzione per un'Visual Studio predefinita.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a49279c9a08c51c5dc81a80bbe0c6db30426b72e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159282"
---
# <a name="best-practices-for-security-in-vspackages"></a>Procedure consigliate per la sicurezza in VSPackage
Per installare nel computer, è necessario essere in esecuzione [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] in un contesto con credenziali amministrative. L'unità di base di sicurezza e distribuzione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un'applicazione è [vspackage](../../extensibility/internals/vspackages.md). Un VSPackage deve essere registrato usando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , che richiede anche credenziali amministrative.

 Gli amministratori hanno le autorizzazioni complete per scrivere nel Registro di sistema e file system ed eseguire qualsiasi codice. È necessario disporre di queste autorizzazioni per sviluppare, distribuire o installare un VSPackage.

 Non appena viene installato, un VSPackage è completamente attendibile. A causa di questo livello elevato di autorizzazione associato a un VSPackage, è possibile installare inavvertitamente un VSPackage con finalità dannose.

 Gli utenti devono assicurarsi di installare i pacchetti VSPackage solo da origini attendibili. Le aziende che sviluppano VSPackage devono assegnare un nome e firmarli in modo che l'utente non eserciti manomissioni. Le aziende che sviluppano VSPackage devono esaminare le dipendenze esterne, ad esempio i servizi Web e l'installazione remota, per valutare e correggere eventuali problemi di sicurezza.

 Per altre informazioni, vedere [Linee guida per la codifica sicura per .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Vedi anche
- [Sicurezza dei componenti aggiuntivi](/previous-versions/1326zbk3(v=vs.140))
- [Sicurezza DDEX](/previous-versions/bb163703(v=vs.140))