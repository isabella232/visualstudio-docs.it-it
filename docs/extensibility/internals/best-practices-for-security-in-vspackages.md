---
title: Procedure consigliate per la sicurezza in VSPackage . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4309feeed3233d2149586afb1bf4efafacb21ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709898"
---
# <a name="best-practices-for-security-in-vspackages"></a>Procedure consigliate per la sicurezza nei pacchetti VSPackageBest practices for security in VSPackages
Per installare [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] il nel computer, è necessario essere in esecuzione in un contesto con credenziali amministrative. L'unità di base di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sicurezza e distribuzione di un'applicazione è il [pacchetto VSPackage](../../extensibility/internals/vspackages.md). Un pacchetto VSPackage deve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]essere registrato utilizzando , che richiede anche credenziali amministrative.

 Gli amministratori dispongono di autorizzazioni complete per scrivere nel Registro di sistema e nel file system ed eseguire qualsiasi codice. È necessario disporre di queste autorizzazioni per sviluppare, distribuire o installare un pacchetto VSPackage.You must have these permissions to develop, deploy, or install a VSPackage.

 Non appena viene installato, un vsPackage è completamente attendibile. A causa di questo alto livello di autorizzazione associato a un VSPackage, è possibile installare inavvertitamente un pacchetto VSPackage con finalità dannose.

 Gli utenti devono assicurarsi di installare VSPackage solo da fonti attendibili. Le aziende che sviluppano VSPackage devono denominarli e firmarli con forza, per assicurare all'utente che la manomissione è impedita. Le aziende che sviluppano package VS devono esaminare le dipendenze esterne, ad esempio i servizi Web e l'installazione remota, per valutare e correggere eventuali problemi di sicurezza.

 Per ulteriori informazioni, vedere Linee guida per [la codifica sicura per .NET Framework.](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90))

## <a name="see-also"></a>Vedere anche
- [Sicurezza dei componenti aggiuntivi](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Sicurezza DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
