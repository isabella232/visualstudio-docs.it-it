---
title: Servizi forniti (VSPackage del controllo del codice sorgente) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 750710cdc381573f8aa6fd064e1fc980030cf359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202700"
---
# <a name="services-provided-source-control-vspackage"></a>Servizi offerti (VSPackage di controllo del codice sorgente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I servizi rappresentano il meccanismo principale attraverso cui viene condivisa la funzionalità tra i pacchetti VSPackage e tra Visual Studio Integrated Development Environment (IDE) e i pacchetti VSPackage installati. Per una descrizione dettagliata dei servizi e la relativa importanza nell'IDE di Visual Studio, vedere[uso e fornitura di servizi](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Il servizio di controllo del codice sorgente  
 Visual Studio offre due livelli di servizi, Servizi a livello di IDE e servizi a livello di pacchetto. L'IDE di Visual Studio fornisce in modo nativo i servizi a livello di IDE. Il pacchetto del controllo del codice sorgente usa alcuni di questi servizi. Il pacchetto del controllo del codice sorgente come VSPackage condivide la propria funzionalità di controllo del codice sorgente fornendo un servizio di controllo del codice sorgente privato. Il pacchetto del controllo del codice sorgente incapsula il set di interfacce correlate al controllo del codice sorgente implementato da esso sotto forma di contratto che può essere utilizzato dall'IDE di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
