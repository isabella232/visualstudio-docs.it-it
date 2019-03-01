---
title: Prerequisiti per le applicazioni a 64 bit la distribuzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f481d944baf60120bf691313400489c876ecf5c2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606251"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>Prerequisiti per la distribuzione di applicazioni a 64 bit
La distribuzione ClickOnce supporta l'installazione di applicazioni su piattaforme a 64 bit. Le piattaforme di destinazione sono **x86** per le piattaforme a 32 bit, **x64** per i computer che supportano i set di istruzioni AMD64 ed EM64T e **Itanium** per il processore Itanium a 64 bit.

## <a name="prerequisites"></a>Prerequisiti
 La tabella seguente elenca i componenti ridistribuibili che è possibile usare come prerequisiti per l'installazione dell'applicazione a 64 bit.

 Se si seleziona un prerequisito che non ha componenti a 64 bit, è possibile che venga visualizzato un avviso che indica che i pacchetti selezionati non sono disponibili per la piattaforma a 64 bit.


| Componente ridistribuibile | Supporto x64 | Supporto IA64 |
| - |-------------|--------------|
| [!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)] | Sì | No |
| Librerie di runtime di Visual C++ 2010 (IA64) | No | Sì |
| Librerie di runtime di Visual C++ 2010 (x64) | Sì | No |
| Microsoft .NET Framework 4 (x86 e x64) | Sì | |
| Microsoft .NET Framework 4 Client Profile (x86 e x64) | Sì | |

## <a name="see-also"></a>Vedere anche
- [Distribuire le applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md)
- [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Applicazioni a 64 bit](/dotnet/framework/64-bit-apps)