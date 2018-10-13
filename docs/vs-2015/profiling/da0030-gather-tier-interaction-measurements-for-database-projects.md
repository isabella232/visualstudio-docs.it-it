---
title: 'DA0030: Raccogli misurazioni di interazione tra livelli per i progetti di database | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f759253ea22e40416a41a6e7dc97ead10249fd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223873"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Raccogli misurazioni di interazione tra livelli per i progetti di database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id regola | DA0030 |  
| Categoria | Utilizzo degli strumenti di profilatura |  
| Metodo di profilatura | Campionamento |  
| Messaggio | La raccolta di misurazioni per le applicazioni multilivello consente di comprendere i modelli di utilizzo di database e i dati chiave accederà ritardi. Provare a profilatura nuovamente l'applicazione con l'opzione profilatura interazione tra livelli abilitata. |  
| Tipo di regola | Informazioni |  
  
## <a name="cause"></a>Causa  
 Le chiamate ai metodi <xref:System.Data> costituiscono una percentuale significativa dei dati di profilatura e non sono stati raccolti dati di interazione tra livelli durante l'esecuzione della profilatura. È consigliabile ripetere la profilatura e aggiungere dati di interazione tra livelli.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola viene attivata ogni volta che viene rilevata un'attività significativa in funzioni che risiedono negli spazi dei nomi System.Data, inclusi <xref:System.Data.Linq><xref:System.Data.Linq>.  
  
 Le applicazioni multilivello usano servizi sovrapposti per i livelli presentazione e dati. Spesso il livello dati è un processo separato che esegue un sistema di gestione di database, ad esempio Microsoft SQL Server. Il livello dati potrebbe anche essere eseguito su un computer separato dal resto dell'applicazione. I profili di campionamento offrono una quantità limitata di informazioni su funzioni e servizi eseguiti out-of-process o in modalità remota.  
  
 Gli strumenti di profilatura possono raccogliere informazioni sugli intervalli per applicazioni multilivello che interagiscono con il livello dati di Microsoft SQL Server usando chiamate asincrone ai servizi ADO.NET. È necessario abilitare in modo esplicito la profilatura dell'interazione tra livelli. Non è attivata per impostazione predefinita.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Questa regola è solo a scopo informativo e potrebbe non richiedere azione correttiva.  
  
 Per informazioni sull'aggiunta di dati di interazione tra livelli ai dati di profilatura dall'IDe di Visual Studio, vedere [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md). Per informazioni sull'aggiunta di dati di interazione tra livelli dalla riga di comando, vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md).



