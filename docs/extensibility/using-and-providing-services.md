---
title: Uso e fornitura di servizi | Microsoft Docs
description: Informazioni sui servizi offerti dall'IDE di Visual Studio per i pacchetti VSPackage da fornire e usare. Questi articoli descrivono come ottenere e fornire servizi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a7c1d9f3632d8b710ac238c372ed4456183a8d1
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715938"
---
# <a name="using-and-providing-services"></a>Uso e offerta di servizi
Un servizio è un contratto tra due pacchetti VSPackage. Un pacchetto VSPackage offre un set specifico di interfacce per l'utilizzo da parte di un altro VSPackage. Ad esempio, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offre il <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> servizio a qualsiasi VSPackage caricato. Questo servizio fornisce l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia, che può essere usata per scrivere nel log attività. Per altre informazioni, vedere [procedura: usare il log attività](../extensibility/how-to-use-the-activity-log.md).

 I pacchetti VSPackage possono offrire servizi propri usando l' <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaccia.

 Visual Studio offre importanti servizi, come i seguenti:

|Servizio IDE|Descrizione|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornisce l'accesso ai servizi IDE che gestiscono le funzionalità di base, i pacchetti VSPackage e il registro di sistema.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce le funzionalità di base relative alla finestra e all'interfaccia utente nell'IDE, ad esempio la possibilità di creare strumenti e finestre dei documenti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce funzionalità di base relative alla soluzione, ad esempio la possibilità di enumerare i progetti, creare nuovi progetti e monitorare le modifiche del progetto.|

## <a name="in-this-section"></a>Contenuto della sezione
- [Essentials servizio](../extensibility/internals/service-essentials.md) Vengono presentati gli elementi importanti di un servizio di Visual Studio.

- [Procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md) Viene illustrato come richiedere (utilizzare) un servizio.

- [Procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md) Viene illustrato come fornire un servizio.

- [Procedura: fornire un servizio di Visual Studio asincrono](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Viene illustrato come fornire un servizio asincrono.

- [Procedura: risolvere i problemi relativi ai servizi](../extensibility/how-to-troubleshoot-services.md) Vengono illustrati i problemi comuni e vengono presentate soluzioni.

## <a name="related-sections"></a>Sezioni correlate
- [SDK di Visual Studio](../extensibility/visual-studio-sdk.md)
