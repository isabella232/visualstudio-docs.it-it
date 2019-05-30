---
title: Procedure consigliate per la sicurezza nei pacchetti VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 144bc62176ebc552e7070b29088acf70329a84d4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309152"
---
# <a name="best-practices-for-security-in-vspackages"></a>Le procedure consigliate per la sicurezza nei pacchetti VSPackage
Per installare il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] nel computer, è necessario essere in esecuzione in un contesto con credenziali amministrative. Unità di base di sicurezza e la distribuzione di un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] applicazione è il [VSPackage](../../extensibility/internals/vspackages.md). Un pacchetto VSPackage deve essere registrato utilizzando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], che richiede credenziali amministrative.

 Gli amministratori hanno autorizzazioni complete per scrivere il Registro di sistema e file system e per eseguire qualsiasi codice. È necessario disporre delle autorizzazioni sviluppare, distribuire o installare un pacchetto VSPackage.

 Non appena è installato, un pacchetto VSPackage è completamente attendibile. A causa di questo livello elevato di autorizzazione associata a un pacchetto VSPackage, è possibile installare inavvertitamente un VSPackage contenente dannosi.

 Gli utenti devono assicurarsi che installano i pacchetti VSPackage solo da fonti attendibili. Società di sviluppo di VSPackages fortemente consigliabile assegnare un nome e firmarli, per assicurare che l'utente che manomissioni non è consentita. Società di sviluppo di VSPackages deve esaminare le dipendenze esterne, ad esempio servizi web e l'installazione remota, valutare e correggere eventuali problemi di sicurezza.

 Per altre informazioni, vedere [linee guida di codifica per .NET Framework protette](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Vedere anche
- [Componente aggiuntivo di sicurezza](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Sicurezza DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)