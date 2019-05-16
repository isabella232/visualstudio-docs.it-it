---
title: Sicurezza e assembly satellite localizzati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9c810c6c7e0c0c73557e6b38860c1e6d3953b225
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691293"
---
# <a name="security-and-localized-satellite-assemblies"></a>Sicurezza e assembly satellite localizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se l'assembly principale usa la funzione di nome sicuro, gli assembly satellite devono essere firmati con la stessa chiave privata dell'assembly principale. Se la coppia chiave pubblica/chiave privata degli assembly satellite e dell'assembly principale non corrisponde, le risorse non verranno caricate. Per altre informazioni sulla firma degli assembly, vedere [Procedura: Firmare un assembly con un nome sicuro](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 In genere, può essere necessario che il gruppo di firma dell'organizzazione o un società di firma esterna usino per la firma la chiave privata. Tale necessità è dovuta alla natura della chiave privata: l'accesso è spesso limitato solo a pochi individui. Durante lo sviluppo è possibile usare la firma posticipata. per altre informazioni, vedere [Ritardo della firma di un assembly](https://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulla sicurezza degli assembly](https://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [Concetti chiave sulla sicurezza](https://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [Introduzione alle applicazioni internazionali basate su .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Applicazioni localizzate](../ide/localizing-applications.md)   
 [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)
