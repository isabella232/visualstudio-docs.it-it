---
title: Estensibilità del servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 691592ce59d4495af3b248dde4ebfc9af1665d55
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015030"
---
# <a name="legacy-language-service-extensibility"></a>Estendibilità dei servizi di linguaggio legacy
Un servizio di linguaggio fornisce supporto specifico del linguaggio per la modifica del codice sorgente nell'IDE.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
 Questa sezione illustra la struttura e l'implementazione di un servizio di linguaggio legacy.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Migrazione di un servizio di linguaggio Legacy](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Viene illustrato come aggiornare un servizio di linguaggio da Visual Studio 2008 alla versione più recente.  
  
 [Nozioni fondamentali sui servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-essentials.md)  
 Fornisce importanti informazioni su come sviluppare servizi di linguaggio per integrare un linguaggio di programmazione in Visual Studio.  
  
 [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Vengono forniti collegamenti ad argomenti che consentono di creare un servizio di linguaggio.  
  
 [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Fornisce informazioni sul supporto per l'evidenziazione della sintassi in un servizio di linguaggio.  
  
 [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fornisce informazioni su come usare il framework di pacchetto gestito (MPF) per implementare un servizio di linguaggio completo nel codice gestito.  
  
 [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Descrive le librerie e strumenti che consentono di sfogliare le viste di struttura ad albero dei simboli nell'IDE.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)  
 Viene fornita una panoramica dell'editor di Visual Studio.  
  
 [Supporto dei servizi di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)  
 Include informazioni e un collegamento per Visual Studio Debugging SDK, che contiene le informazioni necessarie per creare e personalizzare i componenti del debugger per eseguire il debug di programmi.