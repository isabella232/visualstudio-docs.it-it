---
title: Servizi forniti (VSPackage di controllo del codice sorgente) | Microsoft Docs
description: Informazioni su come i pacchetti VSPackage condividono le funzionalità tramite i servizi, inclusa l'interazione con l'IDE Visual Studio e i relativi pacchetti VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 34ef5c26184f06b0a9bec3307f4c6af155f51586
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062758"
---
# <a name="services-provided-source-control-vspackage"></a>Servizi offerti (VSPackage di controllo del codice sorgente)
I servizi sono il meccanismo principale tramite il quale le funzionalità vengono condivise tra i pacchetti VSPackage e tra l'ambiente di sviluppo integrato (IDE) di Visual Studio e i pacchetti VSPackage installati. Per una descrizione dettagliata dei servizi e la relativa importanza nell'IDE Visual Studio, vedere[Uso e fornitura di servizi.](../../extensibility/using-and-providing-services.md)

## <a name="the-source-control-service"></a>Servizio di controllo del codice sorgente
 Visual Studio fornisce due livelli di servizi, i servizi a livello di IDE e i servizi a livello di pacchetto. L Visual Studio IDE fornisce in modo nativo servizi a livello di IDE. Il pacchetto di controllo del codice sorgente utilizza alcuni di questi servizi. Il pacchetto di controllo del codice sorgente come pacchetto VSPackage condivide la propria funzionalità di controllo del codice sorgente fornendo un servizio di controllo del codice sorgente privato. Il pacchetto di controllo del codice sorgente incapsula il set di interfacce correlate al controllo del codice sorgente implementate dal pacchetto sotto forma di contratto che può essere usato dall'IDE Visual Studio codice sorgente.

## <a name="see-also"></a>Vedi anche
- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
