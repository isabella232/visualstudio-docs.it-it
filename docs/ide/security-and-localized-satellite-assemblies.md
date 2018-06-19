---
title: Sicurezza e assembly satellite localizzati
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7eb391f01bc5a709aeaf0002ac647c358355e5f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943748"
---
# <a name="security-and-localized-satellite-assemblies"></a>Sicurezza e assembly satellite localizzati

Se l'assembly principale usa la funzione di nome sicuro, gli assembly satellite devono essere firmati con la stessa chiave privata dell'assembly principale. Se la coppia chiave pubblica/chiave privata degli assembly satellite e dell'assembly principale non corrisponde, le risorse non verranno caricate. Per altre informazioni sulla firma degli assembly, vedere [Procedura: Firmare un assembly con un nome sicuro](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

 In genere, può essere necessario che il gruppo di firma dell'organizzazione o un società di firma esterna usino per la firma la chiave privata. Tale necessità è dovuta alla natura della chiave privata: l'accesso è spesso limitato solo a pochi individui. Durante lo sviluppo è possibile usare la firma posticipata. Per ulteriori informazioni, vedere [Ritardo della firma di un assembly](/dotnet/framework/app-domains/delay-sign-assembly).

## <a name="see-also"></a>Vedere anche

- [Considerazioni sulla sicurezza degli assembly](/dotnet/framework/app-domains/assembly-security-considerations)  - [Concetti principali sulla sicurezza](/dotnet/standard/security/key-security-concepts)
- [Introduzione alle applicazioni internazionali basate su .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [Localizzazione di applicazioni](../ide/localizing-applications.md)
- [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)