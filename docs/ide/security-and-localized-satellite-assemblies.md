---
title: Sicurezza e assembly satellite localizzati | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 54c224b4c830f76c532b268b1e6afe17013ab6c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="security-and-localized-satellite-assemblies"></a>Sicurezza e assembly satellite localizzati
Se l'assembly principale usa la funzione di nome sicuro, gli assembly satellite devono essere firmati con la stessa chiave privata dell'assembly principale. Se la coppia chiave pubblica/chiave privata degli assembly satellite e dell'assembly principale non corrisponde, le risorse non verranno caricate. Per altre informazioni sulla firma degli assembly, vedere [Procedura: Firmare un assembly con un nome sicuro](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).  
  
 In genere, può essere necessario che il gruppo di firma dell'organizzazione o un società di firma esterna usino per la firma la chiave privata. Tale necessità è dovuta alla natura della chiave privata: l'accesso è spesso limitato solo a pochi individui. Durante lo sviluppo è possibile usare la firma posticipata. per altre informazioni, vedere [Ritardo della firma di un assembly](/dotnet/framework/app-domains/delay-sign-assembly).  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulla sicurezza degli assembly](/dotnet/framework/app-domains/assembly-security-considerations)   
 [Concetti chiave sulla sicurezza](/dotnet/standard/security/key-security-concepts)   
 [Introduzione alle applicazioni internazionali basate su .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Applicazioni localizzate](../ide/localizing-applications.md)   
 [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)