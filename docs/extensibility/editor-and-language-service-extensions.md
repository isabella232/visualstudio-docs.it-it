---
title: Editor e linguaggio servizio estensioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4182af1731dec583a555031b90be1315e6a5d9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927480"
---
# <a name="editor-and-language-service-extensions"></a>Estensioni del servizio di editor e linguaggio
È possibile estendere la maggior parte delle funzionalità dell'editor del codice di Visual Studio. L'editor basato su Windows Presentation Foundation (WPF) e viene scritto in codice gestito. Anche se questa progettazione è diverso dalle progettazioni nelle versioni precedenti di Visual Studio, fornisce la maggior parte delle stesse funzionalità. Per estendere l'editor, usare Managed Extensibility Framework (MEF).  
  
 Visual Studio SDK fornisce adapter detto *shim* per supportare i pacchetti VSPackage che sono state scritte per versioni precedenti. Tuttavia, se si dispone di un pacchetto VSPackage esistente, è consigliabile aggiornarla per la nuova tecnologia per ottenere affidabilità e prestazioni migliori.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introduzione all'uso di modelli di elemento dell'Editor.|  
|[Estendere l'editor e servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)|Collegamenti ai documenti che presentano la progettazione e le funzionalità dell'editor di base e mostrano come estendere la soluzione.|  
|[Interfacce legacy nell'editor](../extensibility/legacy-interfaces-in-the-editor.md)|Collegamenti ai documenti che illustrano come accedere all'editor di core da codice esistente.|  
|[Creare finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)|Include collegamenti a documenti che illustrano come creare editor personalizzati.|  
|[Estensibilità del servizio di linguaggio legacy](../extensibility/internals/legacy-language-service-extensibility.md)|Include collegamenti a documenti che descrivono come integrare i linguaggi di programmazione in Visual Studio.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Introduce Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Introduce di Windows Presentation Foundation (WPF).|