---
title: Editor e linguaggio servizio estensioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09456c67eea98947f182e5ab3b3c90fd21a7a7c0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011065"
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