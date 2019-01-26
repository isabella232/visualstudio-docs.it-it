---
title: Contenuti lingue | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7fe1fdfc8b16988505ef30773cf1ec2e98d58edd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039644"
---
# <a name="contained-languages"></a>Linguaggi contenuti

*Contenuti lingue* sono linguaggi contenuti in altri linguaggi. Ad esempio HTML nel [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] le pagine contengano [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] script. Un'architettura dual-lingua è obbligatorio per il *aspx* editor di file per fornire IntelliSense, colorazione e modifica di altre funzionalità per il codice HTML e il linguaggio di scripting.

## <a name="implementation"></a>Implementazione

L'interfaccia più importante, è necessario implementare per i linguaggi contenuti è il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. Questa interfaccia viene implementata da qualsiasi linguaggio che può essere ospitato all'interno di una lingua primaria. Offre un accesso per il servizio di linguaggio colorizzatore filtro di visualizzazione di testo e ID lingua principale del servizio. Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> consente di creare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. I passaggi seguenti mostrano come implementare un linguaggio contenuto:

1.  Uso `QueryService()` per ottenere il linguaggio ID servizio e l'ID dell'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2.  Per creare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> l'interfaccia, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> (metodo). Passare un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia, una o più [elemento ID](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)e un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaccia.

3.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaccia, ovvero oggetto coordinatore del buffer di testo, fornisce i servizi di base necessarie per eseguire il mapping di indirizzi in un file primario nel buffer del linguaggio secondario.

     Ad esempio, in un unico *aspx* file, il file primario include tutto il codice contenuto, HTML e ASP. Tuttavia, il buffer secondario include solo il codice contenuto insieme a eventuali definizioni di classe, per rendere il buffer secondario di un file di codice valido. Il coordinatore del buffer gestisce il lavoro di coordinamento delle modifiche da un buffer a altro.

4.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> metodo, che è la lingua principale, indica il coordinatore del buffer viene eseguito il mapping di testo all'interno del buffer di testo corrispondente nel buffer secondario.

     Il linguaggio passa in una matrice del <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> struttura, che attualmente include solo un'enclosure principale e un intervallo secondario.

5.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> metodo e il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> metodo fornisce il mapping da primario a un buffer secondario e viceversa.