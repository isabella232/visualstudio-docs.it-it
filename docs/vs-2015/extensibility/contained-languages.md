---
title: Linguaggi contenuti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184287"
---
# <a name="contained-languages"></a>Linguaggi contenuti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

I *linguaggi contenuti* sono linguaggi contenuti in altri linguaggi. Ad esempio, HTML nelle [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pagine può contenere [!INCLUDE[csprcs](../includes/csprcs-md.md)] gli [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] script o. Per l'editor di file aspx è necessaria un'architettura a due linguaggi per fornire IntelliSense, colorazione e altre funzionalità di modifica sia per il linguaggio HTML che per il linguaggio di scripting.  
  
## <a name="implementation"></a>Implementazione  
 L'interfaccia più importante che è necessario implementare per i linguaggi contenuti è l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. Questa interfaccia viene implementata da qualsiasi linguaggio che può essere ospitato all'interno di un linguaggio primario. Consente di accedere al colorante del servizio di linguaggio, al filtro di visualizzazione di testo e all'ID del servizio di linguaggio primario. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>Consente di creare un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. Nei passaggi seguenti viene illustrato come implementare un linguaggio contenuto:  
  
1. Utilizzare `QueryService()` per ottenere l'ID del servizio di linguaggio e l'ID di interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> .  
  
2. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> metodo per creare un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. Passare un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia, uno o più [ID elemento](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) e un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaccia.  
  
3. L' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaccia, ovvero l'oggetto coordinatore del buffer di testo, fornisce i servizi di base necessari per eseguire il mapping delle posizioni in un file primario al buffer della lingua secondaria.  
  
     Ad esempio, in un singolo file aspx, il file primario include ASP, HTML e tutto il codice contenuto. Il buffer secondario, tuttavia, include solo il codice contenuto, insieme a qualsiasi definizione di classe, per rendere il buffer secondario un file di codice valido. Il coordinatore del buffer gestisce il lavoro di coordinamento delle modifiche da un buffer all'altro.  
  
4. Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> metodo, che è il linguaggio principale, indica al coordinatore del buffer quale testo all'interno del buffer viene mappato al testo corrispondente nel buffer secondario.  
  
     Il linguaggio passa in una matrice della <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> struttura, che attualmente include solo un intervallo primario e un intervallo secondario.  
  
5. Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> metodo e il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> Metodo forniscono il mapping dal buffer primario a quello secondario e viceversa.
