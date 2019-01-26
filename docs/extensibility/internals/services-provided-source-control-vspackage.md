---
title: Servizi forniti (VSPackage di controllo codice sorgente) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f94efff27ea45dc070e34f26d85be4bd7ff5b50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936905"
---
# <a name="services-provided-source-control-vspackage"></a>Servizi offerti (VSPackage di controllo del codice sorgente)
I servizi sono il meccanismo principale attraverso cui funzionalità viene condivisa tra pacchetti VSPackage e tra l'ambiente di sviluppo integrato (IDE) di Visual Studio e il VSPackage installati. Per una descrizione dettagliata di servizi e la loro importanza nell'IDE di Visual Studio, vedere[sull'utilizzo e la fornitura di servizi](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Il servizio di controllo di origine  
 Visual Studio offre due livelli di servizi, i servizi a livello di IDE e servizi a livello di pacchetto. IDE di Visual Studio in modalità nativa fornisce servizi a livello di IDE. Il pacchetto del controllo sorgente consuma alcuni di questi servizi. Il pacchetto del controllo sorgente come un pacchetto VSPackage condivide la funzionalità di controllo relativa origine, fornendo un servizio di controllo di origine privato proprio. Il pacchetto del controllo sorgente incapsula il set di interfacce relative al controllo origine implementati dall'oggetto sotto forma di un contratto che può essere usato dall'IDE di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)