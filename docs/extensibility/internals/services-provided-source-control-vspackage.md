---
title: Servizi forniti (VSPackage del controllo del codice sorgente) | Microsoft Docs
description: Informazioni su come i pacchetti VSPackage condividono le funzionalità tramite i servizi, tra cui l'interazione con l'IDE di Visual Studio e i relativi pacchetti VSPackage.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4a97ed69d37330132196f0334f5684c0704c5fd2
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876077"
---
# <a name="services-provided-source-control-vspackage"></a>Servizi offerti (VSPackage di controllo del codice sorgente)
I servizi rappresentano il meccanismo principale attraverso cui viene condivisa la funzionalità tra i pacchetti VSPackage e tra Visual Studio Integrated Development Environment (IDE) e i pacchetti VSPackage installati. Per una descrizione dettagliata dei servizi e la relativa importanza nell'IDE di Visual Studio, vedere[uso e fornitura di servizi](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Il servizio di controllo del codice sorgente
 Visual Studio offre due livelli di servizi, Servizi a livello di IDE e servizi a livello di pacchetto. L'IDE di Visual Studio fornisce in modo nativo i servizi a livello di IDE. Il pacchetto del controllo del codice sorgente usa alcuni di questi servizi. Il pacchetto del controllo del codice sorgente come VSPackage condivide la propria funzionalità di controllo del codice sorgente fornendo un servizio di controllo del codice sorgente privato. Il pacchetto del controllo del codice sorgente incapsula il set di interfacce correlate al controllo del codice sorgente implementato da esso sotto forma di contratto che può essere utilizzato dall'IDE di Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
