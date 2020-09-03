---
title: "Procedura: configurare l'analisi del codice per un progetto di codice gestito | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ac04a3d8834e3fc24f148fc36327d101e43720a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658855"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Procedura: Configurare l'analisi codice per un progetto di codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] e [!INCLUDE[vsPro](../includes/vspro-md.md)] è possibile scegliere da un elenco di *set di regole* di analisi codice da applicare a un progetto di codice gestito. Il set di regole predefinito corrisponde alle regole minime consigliate di Microsoft. È possibile applicare un altro set di regole a un progetto o a tutti i progetti in una soluzione.

> [!NOTE]
> Per informazioni su come configurare un set di regole per le applicazioni Web ASP.NET, vedere [procedura: configurare l'analisi del codice per un'applicazione web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Per configurare un set di regole per un progetto .NET Framework

1. In **Esplora soluzioni**fare clic sul progetto.

2. Scegliere **Configura analisi codice per** *NomeProgetto*dal menu **analizza** .

3. Negli elenchi **configurazione** e **piattaforma** fare clic sulla configurazione della build e sulla piattaforma di destinazione.

4. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato usando la configurazione selezionata, selezionare la casella di controllo **Abilita analisi codice su compilazione (definizione CODE_ANALYSIS costante)** . È anche possibile eseguire manualmente l'analisi del codice aprendo il menu **analizza** e facendo clic **su Esegui analisi del codice su** *NomeProgetto*.

5. Per impostazione predefinita, l'analisi del codice non segnala gli avvisi del codice generato automaticamente da strumenti esterni. Per visualizzare gli avvisi dal codice generato, deselezionare la casella di controllo non **visualizzare i risultati del codice generato** .

    > [!NOTE]
    > Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.

6. Nell'elenco **Esegui questo set di regole** effettuare una delle operazioni seguenti:

    - Fare clic sul set di regole che si desidera utilizzare.

    - Fare clic **\<Browse...>** per specificare un set di regole personalizzato esistente non presente nell'elenco.

    - Definire un set di regole personalizzato.

         Per altre informazioni, vedere [creazione di set di regole personalizzati](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Vedere anche
 [Procedura dettagliata: Configurazione e uso di un set di regole personalizzate](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
