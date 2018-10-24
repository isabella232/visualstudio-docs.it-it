---
title: 'DA0030: Raccogli misurazioni di interazione tra livelli per i progetti di database | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d0fb38348a901582182bdfaec2d7d775ec195f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814012"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Raccogli misurazioni di interazione tra livelli per i progetti di database

|||  
|-|-|  
|ID regola|DA0030|  
|Category|Uso degli strumenti di profilatura|  
|Metodo di profilatura|Campionamento|  
|Messaggio|La raccolta di misurazioni per le applicazioni multilivello consente di comprendere i criteri di utilizzo del database e i ritardi di accesso ai dati di chiave. Abilitare l'opzione Profilatura interazione tra livelli e provare a eseguire di nuovo la profilatura dell'applicazione.|  
|Tipo regola|Informazioni|  

## <a name="cause"></a>Causa  
 Le chiamate ai metodi <xref:System.Data> costituiscono una percentuale significativa dei dati di profilatura e non sono stati raccolti dati di interazione tra livelli durante l'esecuzione della profilatura. È consigliabile ripetere la profilatura e aggiungere dati di interazione tra livelli.  

## <a name="rule-description"></a>Descrizione della regola  
 Questa regola viene attivata ogni volta che viene rilevata un'attività significativa in funzioni che risiedono negli spazi dei nomi System.Data, inclusi <xref:System.Data.Linq><xref:System.Data.Linq>.  

 Le applicazioni multilivello usano servizi sovrapposti per i livelli presentazione e dati. Spesso il livello dati è un processo separato che esegue un sistema di gestione di database, ad esempio Microsoft SQL Server. Il livello dati potrebbe anche essere eseguito su un computer separato dal resto dell'applicazione. I profili di campionamento offrono una quantità limitata di informazioni su funzioni e servizi eseguiti out-of-process o in modalità remota.  

 Gli strumenti di profilatura possono raccogliere informazioni sugli intervalli per applicazioni multilivello che interagiscono con il livello dati di Microsoft SQL Server usando chiamate asincrone ai servizi ADO.NET. È necessario abilitare in modo esplicito la profilatura dell'interazione tra livelli. Non è attivata per impostazione predefinita.  

## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Questa regola è solo a scopo informativo e potrebbe non richiedere azione correttiva.  

 Per informazioni sull'aggiunta di dati di interazione tra livelli ai dati di profilatura dall'IDe di Visual Studio, vedere [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md). Per informazioni sull'aggiunta di dati di interazione tra livelli dalla riga di comando, vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md).