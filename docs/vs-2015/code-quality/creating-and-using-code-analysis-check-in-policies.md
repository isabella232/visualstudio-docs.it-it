---
title: Creazione e uso di criteri di archiviazione dell'analisi del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8e31ff799edc93d250eeeab57b349873a63ecf14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667707"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Creazione e utilizzo di criteri di archiviazione di analisi codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si usa controllo della versione di Team Foundation (TFVC), è possibile creare criteri di archiviazione dell'analisi del codice per i progetti di codice .NET Framework e nativi (C/C++) in un progetto team. È possibile usare i criteri di archiviazione dell'analisi del codice per controllare e migliorare la qualità del codice archiviato nella codebase.

 Il criterio passa quando la compilazione locale è aggiornata ed è stata eseguita l'analisi del codice nei file di origine più recenti. Come minimo, le regole di analisi del codice abilitate nel progetto di codice devono contenere le stesse regole definite nei criteri di archiviazione del progetto team. Le regole specificate come errori nelle impostazioni del progetto team devono essere specificate anche come errori nel progetto di codice

> [!IMPORTANT]
> Non è possibile applicare i criteri di archiviazione dell'analisi del codice ai progetti di siti Web. Possono essere applicati ai progetti di applicazione Web.

 Per creare criteri di archiviazione dell'analisi del codice, è possibile usare le impostazioni del progetto team di [!INCLUDE[esprscc](../includes/esprscc-md.md)] . I criteri di archiviazione vengono specificati e applicati per un progetto team, ma le esecuzioni dell'analisi del codice vengono configurate ed eseguite per i singoli progetti di codice nei computer di sviluppo locali. In questa sezione viene descritto come specificare i criteri di archiviazione dell'analisi del codice per un progetto team e come implementare criteri di analisi del codice personalizzati per il codice gestito.

## <a name="in-this-section"></a>Contenuto della sezione
 [Procedura: creare o aggiornare criteri di archiviazione standard dell'analisi del codice](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md) Vengono illustrati i passaggi da eseguire per impostare e modificare i criteri di analisi del codice per un progetto team.

 [Implementazione di criteri di archiviazione personalizzati per il codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md) Vengono illustrati i passaggi da utilizzare per creare un set di regole personalizzato per i criteri di archiviazione di un progetto team e per sincronizzare i progetti di codice del progetto team con i criteri di archiviazione.

 [Compatibilità tra le versioni per i criteri di archiviazione dell'analisi del codice](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md) Vengono illustrati i problemi di compatibilità di archiviazione dell'analisi codice tra le versioni di [!INCLUDE[vstsLong](../includes/vstslong-md.md)] .

 [Procedura: personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md) Viene illustrato come aggiungere parole e token al dizionario a cui viene fatto riferimento nelle regole di denominazione dell'analisi codice.

## <a name="related-sections"></a>Sezioni correlate
 [Impostare e applicare controlli di qualità](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)

 [Miglioramento della qualità del codice con i criteri di archiviazione del progetto team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
