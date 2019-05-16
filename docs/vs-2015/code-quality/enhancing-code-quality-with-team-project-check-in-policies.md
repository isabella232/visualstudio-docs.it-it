---
title: Miglioramento della qualità del codice con criteri di controllo del progetto Team | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 86aac26819e86455c8ab5c3676c8198bbb482e43
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697188"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Miglioramento della qualità del codice con i criteri di archiviazione del progetto team
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si usa il controllo della versione di Team Foundation (TFVC), è possibile creare criteri di archiviazione per i progetti team. per applicare procedure che consentono di ottimizzare il codice e lo sviluppo dei gruppi. I criteri di archiviazione sono regole che vengono impostate a livello di progetto team e applicate nei computer degli sviluppatori prima che sia consentita l'archiviazione del codice.  
  
 È possibile specificare i seguenti criteri di archiviazione del progetto team:  
  
- **Compila**: Richiede che le interruzioni di compilazione create durante una compilazione vengano corrette prima di un nuovo controllo aggiuntivo.  
  
- **I commenti dell'insieme di modifiche**: Richiede che gli utenti forniscano commenti quando archiviano le modifiche.  
  
- **Analisi del codice**: Richiede che venga eseguita l'analisi del codice prima dell'archiviazione.  
  
- **Gli elementi di lavoro**: Richiede che uno o più elementi di lavoro sia associato a check-in.  
  
> [!IMPORTANT]
> Per usare i criteri di archiviazione, è necessario essere connessi a [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)].  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto di supporto|  
|----------|------------------------|  
|**Creare e usare i criteri di archiviazione:** Per creare criteri di controllo usando le impostazioni di progetto Team di [!INCLUDE[esprscc](../includes/esprscc-md.md)].|[Impostare e applicare controlli di qualità](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Creare e usare criteri di controllo dell'analisi del codice:** È possibile scegliere da un set standard di regole di analisi del codice, oppure è possibile creare un set personalizzato.|[Creazione e uso di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Attività|Contenuto di supporto|  
|----------|------------------------|  
|**Configurare l'ambiente di sviluppo:** Prima di poter creare o modificare il codice, è necessario configurare lo sviluppo e ambienti di test usando il codice sorgente appropriato. Se si usano database, è necessario anche avere accesso alla relativa rappresentazione offline.|[Configurazione di ambienti di sviluppo](https://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Usare analisi del codice nel processo di sviluppo:** I membri del team eseguono l'analisi del codice nei propri computer di sviluppo. In Visual Studio gli sviluppatori configurano ed eseguono esecuzioni dell'analisi del codice per i singoli progetti di codice, visualizzano e analizzano i problemi rilevati dalle esecuzioni e creano elementi di lavoro per gli avvisi.|[Analisi della qualità delle applicazioni](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Creare ed eseguire unit test:** Gli unit test offrono a sviluppatori e tester un modo rapido per individuare errori logici nei metodi delle classi in C#, Visual Basic .NET e i progetti C++. Uno unit test può essere creato una volta ed eseguito ogni volta che il codice sorgente viene modificato per assicurarsi che non siano stati introdotti bug.|[Eseguire unit test del codice](../test/unit-test-your-code.md)|  
|**Tenere traccia degli elementi di lavoro e difetti:** È possibile utilizzare gli elementi di lavoro per tenere traccia e gestire il lavoro e le informazioni sul progetto team. Un elemento di lavoro è un record di database che viene usato da [!INCLUDE[esprfound](../includes/esprfound-md.md)] per monitorare l'assegnazione e lo stato del lavoro. Si possono usare diversi tipi di elementi di lavoro per tenere traccia di vari tipi di lavoro, ad esempio requisiti del cliente, bug del prodotto e attività di sviluppo.|[Tenere traccia del lavoro e la gestione del flusso di lavoro &#91;reindirizzato&#93;](https://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>Risorse esterne  
  
### <a name="guidance"></a>Materiale sussidiario  
 [Esecuzione di test per il recapito continuo con Visual Studio 2012 – capitolo 2: Unit test: Test interni](http://go.microsoft.com/fwlink/?LinkID=255188)
