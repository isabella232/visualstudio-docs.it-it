---
title: Editor e estensioni del servizio di linguaggio | Microsoft Docs
description: È possibile estendere la maggior parte delle Visual Studio dell'editor di codice, che viene implementato Windows Presentation Foundation ed è scritto in codice gestito.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: cec77762a356f86d8cab32402c824ec70ae41e8e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634644"
---
# <a name="editor-and-language-service-extensions"></a>Estensioni dell'editor e del servizio di linguaggio
È possibile estendere la maggior parte delle funzionalità dell Visual Studio editor di codice. L'editor è basato sul Windows Presentation Foundation (WPF) ed è scritto in codice gestito. Anche se questa progettazione è diversa dalle progettazioni nelle versioni precedenti di Visual Studio, offre la maggior parte delle stesse funzionalità. Per estendere l'editor, usare Managed Extensibility Framework (MEF).

 L Visual Studio SDK fornisce adattatori noti come *s shims* per supportare i PACCHETTI VSPackage scritti per le versioni precedenti. Tuttavia, se si dispone di un VSPackage esistente, è consigliabile aggiornarlo alla nuova tecnologia per ottenere prestazioni e affidabilità migliori.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introduzione all'uso dei modelli di elemento dell'editor.|
|[Estendere l'editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)|Collegamenti a documenti che introducono la progettazione e le funzionalità dell'editor principale e illustrano come estenderlo.|
|[Interfacce legacy nell'editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)|Collegamenti a documenti che illustrano come accedere all'editor principale dal codice esistente.|
|[Creare editor e finestre di progettazione personalizzati](../extensibility/creating-custom-editors-and-designers.md)|Collegamenti a documenti che illustrano come creare editor personalizzati.|
|[Estendibilità del servizio di linguaggio legacy](../extensibility/internals/legacy-language-service-extensibility.md)|Collegamenti a documenti che descrivono come integrare i linguaggi di programmazione in Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Introduce la Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Introduce l'Windows Presentation Foundation (WPF).|
