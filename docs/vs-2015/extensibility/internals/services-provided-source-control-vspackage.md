---
title: Servizi forniti (VSPackage di controllo codice sorgente) | Microsoft Docs
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
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aff288f68f32d3850cfa92d5999febd1c65572e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529054"
---
# <a name="services-provided-source-control-vspackage"></a>Servizi offerti (VSPackage di controllo del codice sorgente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [i servizi forniti (VSPackage di controllo codice sorgente)](https://docs.microsoft.com/visualstudio/extensibility/internals/services-provided-source-control-vspackage).  
  
I servizi sono il meccanismo principale attraverso cui funzionalità viene condivisa tra pacchetti VSPackage e tra l'ambiente di sviluppo integrato (IDE) di Visual Studio e il VSPackage installati. Per una descrizione dettagliata di servizi e la loro importanza nell'IDE di Visual Studio, vedere[sull'utilizzo e la fornitura di servizi](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Il servizio di controllo di origine  
 Visual Studio offre due livelli di servizi, i servizi a livello di IDE e servizi a livello di pacchetto. IDE di Visual Studio in modalità nativa fornisce servizi a livello di IDE. Il pacchetto del controllo sorgente consuma alcuni di questi servizi. Il pacchetto del controllo sorgente come un pacchetto VSPackage condivide la funzionalità di controllo relativa origine, fornendo un servizio di controllo di origine privato proprio. Il pacchetto del controllo sorgente incapsula il set di interfacce relative al controllo origine implementati dall'oggetto sotto forma di un contratto che può essere usato dall'IDE di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)

