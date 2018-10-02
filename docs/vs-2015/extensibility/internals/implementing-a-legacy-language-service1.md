---
title: Implementazione di un tipo di linguaggio legacy1 | Microsoft Docs
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
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c77e935946d06dd2448c1f9bda85fd8b6b69aa2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520256"
---
# <a name="implementing-a-legacy-language-service"></a>Implementazione di un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [implementazione di un tipo di linguaggio legacy1](https://docs.microsoft.com/visualstudio/extensibility/internals/implementing-a-legacy-language-service1).  
  
È possibile utilizzare le classi nel framework di pacchetto gestito (MPF) per implementare un servizio di linguaggio legacy che supporta un'ampia gamma di funzionalità, quali l'evidenziazione della sintassi, corrispondenza parentesi graffe e completamento di IntelliSense.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Panoramica dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)  
 Panoramica delle funzionalità del servizio di linguaggio supportati in MPF.  
  
 [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Vengono descritte le funzionalità necessarie per implementare un servizio di linguaggio tramite MPF.  
  
 [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Vengono descritti i passaggi necessari per registrare un servizio di linguaggio basato su MPF con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Descrive i due parser che sono necessari per implementare tutte le funzionalità di un servizio di linguaggio tramite MPF.  
  
 [Procedura dettagliata: Creazione di un servizio di linguaggio legacy](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Fornisce i passaggi di base necessarie per implementare un servizio di linguaggio MPF in un pacchetto VSPackage.  
  
 [Procedura dettagliata: Recupero di un elenco di frammenti di codice installati (implementazione legacy)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Vengono illustrate le tecniche di recupero di un elenco di frammenti di codice installati.  
  
 [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)  
 Vengono forniti collegamenti ad argomenti che illustrano in dettaglio la procedura necessaria per implementare tutte le funzionalità di un servizio di linguaggio tramite MPF.

