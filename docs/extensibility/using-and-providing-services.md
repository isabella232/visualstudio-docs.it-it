---
title: Utilizzo e fornitura di servizi Documenti Microsoft
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
ms.openlocfilehash: 8741d8d66af96ad4c6abea44b238393a34c5aa95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698732"
---
# <a name="using-and-providing-services"></a>Uso e offerta di servizi
A service is a contract between two VSPackages. Un pacchetto VSPackage offre un set specifico di interfacce per un altro VSPackage da utilizzare. Ad esempio, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> offre il servizio a qualsiasi VSPackage caricato. Questo servizio <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> fornisce l'interfaccia, che può essere utilizzata per scrivere nel log attività. Per ulteriori informazioni, vedere [Procedura: utilizzare il log attività](../extensibility/how-to-use-the-activity-log.md).

 VSPackage possono offrire servizi propri <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> utilizzando l'interfaccia..

 Visual Studio offre servizi importanti, ad esempio:

|Servizio IDE|Descrizione|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornisce l'accesso ai servizi IDE che gestiscono funzionalità di base, VSPackage e il Registro di sistema.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce funzionalità di base correlate alle finestre e all'interfaccia utente nell'IDE, ad esempio la possibilità di creare strumenti e finestre di documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce funzionalità di base correlate alla soluzione, ad esempio la possibilità di enumerare progetti, creare nuovi progetti e monitorare le modifiche al progetto.|

## <a name="in-this-section"></a>Contenuto della sezione
- [Nozioni di base sul servizio](../extensibility/internals/service-essentials.md) Presenta gli elementi importanti di un servizio di Visual Studio.

- [Procedura: ottenere un servizioHow to: Get a Service](../extensibility/how-to-get-a-service.md) Viene illustrato come richiedere (utilizzare) un servizio.

- [Procedura: fornire un servizioHow to: Provide a Service](../extensibility/how-to-provide-a-service.md) Viene illustrato come fornire un servizio.

- [Procedura: fornire un servizio asincrono di Visual StudioHow to: Provide an Asynchronous Visual Studio Service](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Viene illustrato come fornire un servizio asincrono.

- [Procedura: Risolvere i problemi relativi ai serviziHow to: Troubleshoot Services](../extensibility/how-to-troubleshoot-services.md) Vengono illustrati i problemi comuni e vengono presentate soluzioni.

## <a name="related-sections"></a>Sezioni correlate
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
