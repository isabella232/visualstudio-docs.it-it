---
title: Procedure consigliate per la sicurezza nei pacchetti VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e294995a25b0369ab839680a97fe670f9a99508d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519859"
---
# <a name="best-practices-for-security-in-vspackages"></a>Procedure consigliate per la sicurezza nei pacchetti VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedure consigliate per la sicurezza nei pacchetti VSPackage](https://docs.microsoft.com/visualstudio/extensibility/internals/best-practices-for-security-in-vspackages).  
  
Per installare il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] nel computer, è necessario essere in esecuzione in un contesto con credenziali amministrative. Unità di base di sicurezza e la distribuzione di un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] applicazione è il [VSPackage](../../extensibility/internals/vspackages.md). Un pacchetto VSPackage deve essere registrato utilizzando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], che richiede credenziali amministrative.  
  
 Gli amministratori hanno autorizzazioni complete per scrivere il Registro di sistema e file system e per eseguire qualsiasi codice. È necessario disporre delle autorizzazioni sviluppare, distribuire o installare un pacchetto VSPackage.  
  
 Non appena è installato, un pacchetto VSPackage è completamente attendibile. A causa di questo livello elevato di autorizzazione associata a un pacchetto VSPackage, è possibile installare inavvertitamente un VSPackage contenente dannosi.  
  
 Gli utenti devono assicurarsi che installano i pacchetti VSPackage solo da fonti attendibili. Società di sviluppo di VSPackages fortemente consigliabile assegnare un nome e firmarli, per assicurare che l'utente che manomissioni non è consentita. Società di sviluppo di VSPackages deve esaminare le dipendenze esterne, ad esempio servizi web e l'installazione remota, valutare e correggere eventuali problemi di sicurezza.  
  
 Per altre informazioni, vedere proteggere le linee guida di codifica per .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza componenti aggiuntivi](http://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [Sicurezza DDEX](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)

