---
title: Contenuti lingue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0b455a526bf1b32de90588a103c23855e730946
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530195"
---
# <a name="contained-languages"></a>Linguaggi contenuti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

La versione più recente di questo argomento è reperibile in [linguaggi contenuti](https://docs.microsoft.com/visualstudio/extensibility/contained-languages).  
  
*Contenuti lingue* sono linguaggi contenuti in altri linguaggi. Ad esempio HTML nel [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] le pagine contengano [!INCLUDE[csprcs](../includes/csprcs-md.md)] o [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] script. Un'architettura dual-lingua è obbligatoria per l'editor di file con estensione aspx fornire IntelliSense, colorazione e altre funzionalità di modifica per il codice HTML e il linguaggio di scripting.  
  
## <a name="implementation"></a>Implementazione  
 L'interfaccia più importante, è necessario implementare per i linguaggi contenuti è il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. Questa interfaccia viene implementata da qualsiasi linguaggio che può essere ospitato all'interno di una lingua primaria. Offre un accesso per il servizio di linguaggio colorizzatore filtro di visualizzazione di testo e ID lingua principale del servizio. Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> consente di creare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. I passaggi seguenti mostrano come implementare un linguaggio contenuto:  
  
1.  Uso `QueryService()` per ottenere il linguaggio ID servizio e l'ID dell'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> metodo per creare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. Passare un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia, una o più [elemento ID](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) e un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaccia.  
  
3.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaccia, ovvero oggetto coordinatore del buffer di testo, fornisce i servizi di base necessarie per eseguire il mapping di indirizzi in un file primario nel buffer del linguaggio secondario.  
  
     Ad esempio, in un unico file aspx, il file primario include ASP, HTML e tutto il codice contenuto. Tuttavia, il buffer secondario, include solo il codice contenuto, insieme a eventuali definizioni di classe, per rendere il buffer secondario di un file di codice valido. Il coordinatore del buffer gestisce il lavoro di coordinamento delle modifiche da un buffer a altro.  
  
4.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> metodo, che è la lingua principale, indica il coordinatore del buffer viene eseguito il mapping di testo all'interno del buffer di testo corrispondente nel buffer secondario.  
  
     Il linguaggio passa in una matrice del <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> struttura, che attualmente include solo un'enclosure principale e un intervallo secondario.  
  
5.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> metodo e il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> metodo fornisce il mapping da primario a un buffer secondario e viceversa.

