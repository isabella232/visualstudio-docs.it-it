---
title: Procedure consigliate per la sicurezza nei pacchetti VSPackage | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709898"
---
# <a name="best-practices-for-security-in-vspackages"></a>Procedure consigliate per la sicurezza nei pacchetti VSPackage
Per installare nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] computer, è necessario che sia in esecuzione in un contesto con credenziali amministrative. L'unità di base di sicurezza e distribuzione di un' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] applicazione è il [pacchetto VSPackage](../../extensibility/internals/vspackages.md). Un pacchetto VSPackage deve essere registrato tramite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , che richiede anche credenziali amministrative.

 Gli amministratori dispongono di autorizzazioni complete per scrivere nel registro di sistema e file system e per eseguire il codice. È necessario disporre di queste autorizzazioni per sviluppare, distribuire o installare un pacchetto VSPackage.

 Non appena viene installato, un pacchetto VSPackage è completamente attendibile. A causa di questo elevato livello di autorizzazioni associato a un VSPackage, è possibile installare inavvertitamente un VSPackage con finalità dannose.

 Gli utenti devono assicurarsi di installare i pacchetti VSPackage solo da origini attendibili. Le aziende che sviluppano pacchetti VSPackage dovrebbero assegnare un nome sicuro e firmarle, per garantire che l'utente possa manomettere. Le aziende che sviluppano pacchetti VSPackage devono esaminare le dipendenze esterne, ad esempio i servizi Web e l'installazione remota, per valutare e correggere eventuali problemi di sicurezza.

 Per ulteriori informazioni, vedere [linee guida per la codifica sicura per la .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Vedere anche
- [Sicurezza del componente aggiuntivo](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Sicurezza di DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
