---
title: Creazione e utilizzo di criteri di controllo dell'analisi del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2aef2183cde96bfb5faa1bb62fa341f901dd7018
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955278"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Creazione e utilizzo di criteri di archiviazione di analisi codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si usa Team Foundation Version Control (TFVC), è possibile creare un criterio di controllo dell'analisi codice per .NET Framework e progetti di codice nativi (C/C++) in un progetto team. È possibile usare i criteri di controllo dell'analisi codice per controllare e migliorare la qualità del codice che viene archiviato nella codebase.  
  
 I criteri vengono soddisfatti quando la compilazione locale è aggiornata e l'analisi del codice è stato eseguito nel file di origine più recente. Come minimo, le regole di analisi codice abilitate nel progetto di codice devono contenere le stesse regole di quelli definiti nel check-in Criteri di progetto team. Le regole che sono state specificate come errori nelle impostazioni del progetto Team devono essere specificate anche come errori nel progetto di codice  
  
> [!IMPORTANT]
>  Non è possibile applicare criteri di controllo dell'analisi del codice per progetti di siti web. Possono essere applicati a web application projects.  
  
 Per creare codice criteri di archiviazione al posto dell'analisi utilizzando le impostazioni di progetto Team di [!INCLUDE[esprscc](../includes/esprscc-md.md)]. I criteri di archiviazione sono specificati e applicati per un progetto team, ma esecuzioni dell'analisi del codice sono configurate ed eseguite per singoli progetti di codice nei computer di sviluppo locale. In questa sezione viene descritto come specificare criteri analisi codice controllo-per un progetto team e come implementare criteri analisi codice personalizzati per codice gestito.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura: Crea o aggiorna i criteri di controllo dell'analisi del codice Standard](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Illustra i passaggi da utilizzare per impostare e modificare i criteri di analisi codice per un progetto team.  
  
 [Implementazione di criteri di archiviazione personalizzati per codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Illustra i passaggi da utilizzare per creare una regola personalizzata impostata per i criteri di controllo di un progetto team e per sincronizzare i progetti di codice del progetto team con i criteri di controllo.  
  
 [Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Vengono illustrati i problemi di controllo di compatibilità di analisi codice tra le versioni di [!INCLUDE[vstsLong](../includes/vstslong-md.md)].  
  
 [Procedura: Personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Viene illustrato come aggiungere parole e token al dizionario in cui viene fatto riferimento nelle regole di denominazione di analisi codice.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Impostare e applicare controlli di qualità](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Miglioramento della qualità del codice con i criteri di archiviazione del progetto team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
