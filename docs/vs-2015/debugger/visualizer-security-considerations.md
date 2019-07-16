---
title: Considerazioni sulla sicurezza del Visualizzatore | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51c79c34520c36e51599d4d6135784f493673b62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146456"
---
# <a name="visualizer-security-considerations"></a>Considerazioni sulla sicurezza del visualizzatore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La scrittura di un visualizzatore comporta possibili rischi per la sicurezza. Attualmente non sono noti attacchi in grado di sfruttare tali rischi, ma gli sviluppatori devono essere a conoscenza della loro esistenza e adottare misure di sicurezza adeguate come descritto in questo argomento al fine di impedire eventuali attacchi futuri.  
  
 Per i visualizzatori del debugger sono richiesti maggiori privilegi rispetto a quelli consentiti da un'applicazione parzialmente attendibile. I visualizzatori non vengono caricati in caso di interruzione in codice con attendibilità parziale. Per eseguire il debug tramite un visualizzatore, è necessario eseguire il codice con attendibilità totale.  
  
## <a name="possible-malicious-debuggee-component"></a>Possibile componente oggetto del debug dannoso  
 I visualizzatori sono costituiti da almeno due classi, una sul lato debugger e una sull'oggetto del debug. I visualizzatori sono spesso distribuiti in assembly distinti inseriti in speciali directory, ma possono anche essere caricati all'esterno dell'oggetto del debug. In tali circostanze, il debugger estrae il codice dall'oggetto del debug e lo esegue al suo interno con attendibilità totale.  
  
 L'esecuzione di codice del lato oggetto del debug con attendibilità totale risulta problematica quando l'oggetto del debug non è totalmente attendibile. Un visualizzatore che tenti di caricare un assembly con attendibilità parziale dall'oggetto del debug nel debugger verrà terminato.  
  
 Esiste tuttavia ancora una minore vulnerabilità. Il lato oggetto del debug può essere associato a un lato debugger caricato da un'altra origine, diversa dall'oggetto del debug. Il lato oggetto del debug può quindi indicare al lato debugger attendibile di eseguire operazioni per proprio conto. Se la classe del lato debugger attendibile espone un meccanismo di eliminazione file, ad esempio, l'oggetto del debug ad attendibilità parziale può richiamare tale meccanismo quando l'utente ne richiama il visualizzatore.  
  
 Per ovviare a questa vulnerabilità, tenere presenti le interfacce esposte dal visualizzatore.  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura del visualizzatore](../debugger/visualizer-architecture.md)   
 [Procedura: Scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)   
 [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
