---
title: Uso e fornitura di servizi | Microsoft Docs
description: Informazioni sui servizi che l'IDE Visual Studio per i pacchetti VSPackage da fornire e usare. Questi articoli descrivono come ottenere e fornire servizi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c230e0e573c19fe5f53e70d6c7a4ec1f6814d6d6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109955"
---
# <a name="using-and-providing-services"></a>Uso e offerta di servizi
Un servizio è un contratto tra due pacchetti VSPackage. Un VSPackage offre un set specifico di interfacce che un altro VSPackage può usare. Ad esempio, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offre il servizio a qualsiasi <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> VSPackage caricato. Questo servizio fornisce <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> l'interfaccia , che può essere usata per scrivere nel log attività. Per altre informazioni, [vedere Procedura: Usare il log attività.](../extensibility/how-to-use-the-activity-log.md)

 I pacchetti VSPackage possono offrire servizi personalizzati usando <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> l'interfaccia .

 Visual Studio offre servizi importanti, ad esempio i seguenti:

|Servizio IDE|Descrizione|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornisce l'accesso ai servizi IDE che gestiscono le funzionalità di base, i pacchetti VSPackage e il Registro di sistema.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce funzionalità di base relative alle finestre e all'interfaccia utente nell'IDE, ad esempio la possibilità di creare strumenti e finestre dei documenti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce funzionalità di base correlate alla soluzione, ad esempio la possibilità di enumerare i progetti, creare nuovi progetti e monitorare le modifiche ai progetti.|

## <a name="in-this-section"></a>Contenuto della sezione
- [Informazioni di base sul servizio](../extensibility/internals/service-essentials.md) Presenta gli elementi importanti di un Visual Studio servizio.

- [Procedura: Ottenere un servizio](../extensibility/how-to-get-a-service.md) Viene illustrato come richiedere (utilizzare) un servizio.

- [Procedura: Fornire un servizio](../extensibility/how-to-provide-a-service.md) Viene illustrato come fornire un servizio.

- [Procedura: Fornire un servizio di Visual Studio asincrono](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Viene illustrato come fornire un servizio asincrono.

- [Procedura: Risolvere i problemi relativi ai servizi](../extensibility/how-to-troubleshoot-services.md) Vengono illustrati i problemi comuni e vengono presentate le soluzioni.

## <a name="related-sections"></a>Sezioni correlate
- [Visual Studio Sdk](../extensibility/visual-studio-sdk.md)
