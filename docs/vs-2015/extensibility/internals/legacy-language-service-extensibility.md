---
title: Estendibilità del servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 43
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9346311aac4bc5833005423e90c2eb92faddcb84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194988"
---
# <a name="legacy-language-service-extensibility"></a>Estendibilità dei servizi di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servizio di linguaggio fornisce supporto specifico della lingua per la modifica del codice sorgente nell'IDE.  
  
 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
 In questa sezione viene illustrata la struttura e l'implementazione di un servizio di linguaggio legacy.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Migrazione di un servizio di linguaggio legacy](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Viene illustrato come aggiornare un servizio di linguaggio da Visual Studio 2008 alla versione più recente.  
  
 [Nozioni fondamentali sui servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-essentials.md)  
 Vengono fornite informazioni importanti su come sviluppare servizi di linguaggio per integrare un linguaggio di programmazione in Visual Studio.  
  
 [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Vengono forniti collegamenti ad argomenti che consentono di creare un servizio di linguaggio.  
  
 [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Vengono fornite informazioni sul supporto dell'evidenziazione della sintassi in un servizio di linguaggio.  
  
 [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Vengono fornite informazioni su come utilizzare il Framework di pacchetto gestito (MPF) per implementare un servizio di linguaggio completo nel codice gestito.  
  
 [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Vengono descritte le librerie e gli strumenti che consentono di esplorare le visualizzazioni ad albero dei simboli nell'IDE.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)  
 Viene fornita una panoramica degli editor di Visual Studio.  
  
 [Supporto dei servizi di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)  
 Vengono fornite informazioni su e un collegamento a Visual Studio Debugging SDK, che contiene le informazioni necessarie per creare e personalizzare i componenti del debugger utilizzati per eseguire il debug dei programmi.
