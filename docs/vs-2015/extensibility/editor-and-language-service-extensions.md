---
title: Editor e estensioni del servizio di linguaggio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7fa3e4be6ee44011eb1286e3ebf22ee69f8e3397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683112"
---
# <a name="editor-and-language-service-extensions"></a>Estensioni dell'editor e dei servizi di linguaggio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile estendere la maggior parte delle funzionalità dell'editor di codice di Visual Studio. L'editor è basato sul Windows Presentation Foundation (WPF) ed è scritto in codice gestito. Sebbene questa progettazione sia diversa da quella delle versioni precedenti di Visual Studio, fornisce la maggior parte delle stesse funzionalità. Per estendere l'editor, utilizzare il Managed Extensibility Framework (MEF).  
  
 Visual Studio SDK fornisce adattatori noti come *shim* per supportare i pacchetti VSPackage scritti per le versioni precedenti. Tuttavia, se si dispone di un pacchetto VSPackage esistente, è consigliabile aggiornarlo alla nuova tecnologia per ottenere prestazioni e affidabilità migliori.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introduzione all'utilizzo dei modelli di elemento dell'editor.|  
|[Estensione dell'editor e dei servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)|Collegamenti ai documenti che introducono la progettazione e le funzionalità dell'editor principale e illustrano come estenderlo.|  
|[Interfacce legacy nell'editor](../extensibility/legacy-interfaces-in-the-editor.md)|Collegamenti ai documenti che illustrano come accedere all'editor principale da codice esistente.|  
|[Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)|Collegamenti ai documenti in cui viene illustrato come creare editor personalizzati.|  
|[Estendibilità dei servizi di linguaggio legacy](../extensibility/internals/legacy-language-service-extensibility.md)|Collegamenti ai documenti che descrivono come integrare i linguaggi di programmazione in Visual Studio.|  
|[Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Introduce il Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Introduce il Windows Presentation Foundation (WPF).|
