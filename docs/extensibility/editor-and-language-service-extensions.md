---
title: Editor e estensioni del servizio di linguaggio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e37165dc5fe9ac010545304218e807d923b424b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712029"
---
# <a name="editor-and-language-service-extensions"></a>Editor e estensioni del servizio di linguaggio
È possibile estendere la maggior parte delle funzionalità dell'editor di codice di Visual Studio.You can extend most features of the Visual Studio code editor. L'editor è basato su Windows Presentation Foundation (WPF) ed è scritto in codice gestito. Anche se questa progettazione è diversa dalle progettazioni nelle versioni precedenti di Visual Studio, fornisce la maggior parte delle stesse funzionalità. Per estendere l'editor, utilizzare Managed Extensibility Framework (MEF).

 Visual Studio SDK fornisce adattatori noti come *shim* per supportare i pacchetti VSPackage scritti per le versioni precedenti. Tuttavia, se si dispone di un VSPackage esistente, si consiglia di aggiornarlo alla nuova tecnologia per ottenere prestazioni e affidabilità migliori.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Creare un'estensione con un modello di elemento dell'editorCreate an extension with an editor item template](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introduzione all'utilizzo dei modelli di elemento Dell'editor.|
|[Estendere l'editor e i servizi di linguaggioExtend the editor and language services](../extensibility/extending-the-editor-and-language-services.md)|Collegamenti a documenti che introducono la progettazione e le funzionalità dell'editor principale e mostrano come estenderlo.|
|[Interfacce legacy nell'editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|Collegamenti a documenti che spiegano come accedere all'editor principale dal codice esistente.|
|[Creare editor e finestre di progettazione personalizzatiCreate custom editors and designers](../extensibility/creating-custom-editors-and-designers.md)|Collegamenti a documenti che illustrano come creare editor personalizzati.|
|[Estendibilità del servizio di linguaggio legacyLegacy language service extensibility](../extensibility/internals/legacy-language-service-extensibility.md)|Collegamenti a documenti che descrivono come integrare i linguaggi di programmazione in Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Introduce il framework di estensibilità gestita (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Introduce Windows Presentation Foundation (WPF).|
