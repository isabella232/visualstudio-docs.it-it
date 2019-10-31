---
title: Editor e estensioni del servizio di linguaggio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b6a64d92e26ff1714a77adbef88e02fca966f1f
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186711"
---
# <a name="editor-and-language-service-extensions"></a>Editor e estensioni del servizio di linguaggio
È possibile estendere la maggior parte delle funzionalità dell'editor di codice di Visual Studio. L'editor è basato sul Windows Presentation Foundation (WPF) ed è scritto in codice gestito. Sebbene questa progettazione sia diversa da quella delle versioni precedenti di Visual Studio, fornisce la maggior parte delle stesse funzionalità. Per estendere l'editor, utilizzare il Managed Extensibility Framework (MEF).

 Visual Studio SDK fornisce adattatori noti come *shim* per supportare i pacchetti VSPackage scritti per le versioni precedenti. Tuttavia, se si dispone di un pacchetto VSPackage esistente, è consigliabile aggiornarlo alla nuova tecnologia per ottenere prestazioni e affidabilità migliori.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introduzione all'utilizzo dei modelli di elemento dell'editor.|
|[Estendere l'editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)|Collegamenti ai documenti che introducono la progettazione e le funzionalità dell'editor principale e illustrano come estenderlo.|
|[Interfacce legacy nell'editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|Collegamenti ai documenti che illustrano come accedere all'editor principale da codice esistente.|
|[Creazione di editor e finestre di progettazione personalizzati](../extensibility/creating-custom-editors-and-designers.md)|Collegamenti ai documenti in cui viene illustrato come creare editor personalizzati.|
|[Estendibilità del servizio di linguaggio legacy](../extensibility/internals/legacy-language-service-extensibility.md)|Collegamenti ai documenti che descrivono come integrare i linguaggi di programmazione in Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Introduce il Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Introduce il Windows Presentation Foundation (WPF).|