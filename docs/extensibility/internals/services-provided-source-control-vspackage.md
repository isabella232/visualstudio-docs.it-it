---
title: Servizi forniti (controllo del codice sorgente VSPackage) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f08ebe49756b442ef474ac2a032a72894f6bec15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705403"
---
# <a name="services-provided-source-control-vspackage"></a>Servizi offerti (VSPackage di controllo del codice sorgente)
I servizi sono il meccanismo principale tramite il quale la funzionalità viene condivisa tra i package VS e tra l'ambiente di sviluppo integrato (IDE) di Visual Studio e i package VS installati. Per una descrizione dettagliata dei servizi e della relativa importanza nell'IDE di Visual Studio, vedere[Utilizzo e fornitura di servizi](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Servizio controllo del codice sorgenteThe Source Control Service
 Visual Studio fornisce due livelli di servizi, servizi a livello di IDE e servizi a livello di pacchetto. L'IDE di Visual Studio fornisce in modo nativo i servizi a livello di IDE. Il pacchetto di controllo del codice sorgente utilizza alcuni di questi servizi. Il pacchetto di controllo di origine come un VSPackage condivide la funzionalità di controllo del codice sorgente fornendo un servizio di controllo del codice sorgente privato proprio. Il pacchetto di controllo di origine incapsula il set di interfacce correlate al controllo del codice sorgente implementate da esso sotto forma di un contratto che può essere utilizzato dall'IDE di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
